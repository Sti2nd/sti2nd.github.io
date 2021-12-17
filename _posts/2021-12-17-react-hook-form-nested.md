---
layout: post
title:  "Validation in react-hook-form with nested form fields"
description: ""
date: 2021-12-17 20:26:00 +0100
categories: []
tags: [react, react-hook-form, form, validation, nested, schema]
permalink: /react-hook-form-nested-validation/
lang: en_GB
image: 
author: "Stian Jørgensrud"
---

In the projects I have worked on forms quickly grow to be large components. The big size introduces the need for splitting the form into smaller components. Previously I passed down the register method to the child components because I used the [validation option of the register method](https://react-hook-form.com/get-started#Applyvalidation). Now that I have tested out [schema validation](https://react-hook-form.com/get-started#SchemaValidation) I can safely say that schema validation is the better option for nested form fields.

> TL;DR: Use schema validation in react-hook-form for forms with nested form fields.

## From basic to schema validation

Following are code examples where we go from a basic form in one component to a form that consists of several components and uses schema validation.

First we have a simple example with react-hook-form using native elements:

```jsx
<form>
  <label for="inputId">Name</label>
  <input
    type="text"
    id="inputId"
    {...register("name", { required: true, maxLength: 32 })}
  />
</form>;
```

Using version 7 of react-hook-form one must spread the register method into the input element, and like in old versions we can specify validation rules as the second argument.

I rarely use the native HTML-input elements directly and instead use a component library like [react-bootstrap](https://github.com/react-bootstrap/react-bootstrap). Then a single input becomes the following:

```jsx
<Form>
  <Form.Group controlId="inputId">
    <Form.Label>Name</Form.Label>
    <Form.Control
      type="text"
      {...register("name", { required: true, maxLength: 32 })}
    />
  </Form.Group>
</Form>;
```

And it is pretty much essential to have feedback on the field if there are validation errors so let's add that. And if we also add some of the usual HTML attributes we end up with this:

```jsx
<Form>
  <Form.Group controlId="inputId">
    <Form.Label>Name</Form.Label>
    <Form.Control 
      autoFocus 
      type="text" 
      {...register("name", { required: true, maxLength: 32 })}
      isValid={!errors?.name} 
      isInvalid={!!errors?.name} 
      defaultValue="" 
      placeholder="Write your name here" 
    />
    <Form.Control.Feedback type="invalid">
      {errors?.name?.message}
    </Form.Control.Feedback>
  </Form.Group>
</Form>
```

This is only one input field! So it is not surprising the forms become quite large. At this point we probably want to move the repeated JSX into a reusable component. I often put the `Form.Group` (with the code inside it) into a reusable component called `FormField`.

The example below is how I did nested form fields before; you may skip it. I also added the useForm hook explicitly because I think it makes it clearer.

```jsx
// Bad code, react-hook-form 6
const { register, handleSubmit } = useForm();

return (
  <Form onSubmit={handleSubmit((data) => { console.log(data) })}>
    <FormField
      labelText="Name"
      errors={errors}
      inputRef={register("name", { required: true, maxLength: 32 })}
    />
  </Form>
);
```

As seen above, the register method is passed down from the parent component to the child component (FormField), which will set it on the input ref. This doesn't work with react-hook-form version 7 because it requires one to apply spread to the register method[^1].

One solution to make the above work in version 7 is to use schema validation. There a numerous schema libraries supported, see all of them in the [resolvers repository](https://github.com/react-hook-form/resolvers). I went with [zod](https://github.com/colinhacks/zod) because it is able to infer the form type from the schema.

```jsx
// Good code 1, react-hook-form 7
// import { z } from "zod";
// import { zodResolver } from "@hookform/resolvers/zod";

const formSchema = z.object({
  name: z.string().max(32),
});
const FormType = z.infer<typeof formSchema>;

const { register, handleSubmit } = useForm<FormType>({
  resolver: zodResolver(formSchema),
});

return (
  <Form onSubmit={handleSubmit((data: FormType) => { 
      console.log(data) 
    })}
  >
    <FormField
      name="name"
      labelText="Name"
      errors={errors}
      register={register}
    />
  </Form>
);
```

Because of the fact that validation with schema will happen after all the inputs have been registered, we only need to register the field inside the FormField component; `{...register("name")}`, not pass any validation. And by the way, I added imports in comments so you can see where `z` and `zodResolver` are coming from.

And lastly, I tend to use the [FormContext API](https://react-hook-form.com/api/useformcontext) right away so I don't need to pass the register method down in all children.

```jsx
// Good code 2, react-hook-form 7
// import { z } from "zod";
// import { zodResolver } from "@hookform/resolvers/zod";

const formSchema = z.object({
  name: z.string().max(32),
});
const FormType = z.infer<typeof formSchema>;

const formMethods = useForm<FormType>({
  resolver: zodResolver(formSchema),
});
const { register, handleSubmit } = formMethods;

return (
  <FormProvider {...formMethods}>
    <Form onSubmit={handleSubmit((data: FormType) => { 
        console.log(data) 
      })}
    >
      <FormField name="name" labelText="Name" errors={errors} />
    </Form>
  </FormProvider>
);
```

Now you know how to use schema validation with react-hook-form so you can manage large forms with ease. ✅🚀

## Gotcha: input element always return string

When you write your zod schema to validate something else than a `string` type you will experience that it doesn't work. This is because the native HTML-input field always returns a `string`! React-hook-form has two quick options you can use that will <u>try</u> to convert the value to another type; `valueAsNumber` and `valueAsDate` on the [register method](https://react-hook-form.com/api/useform/register). If the field is optional, though, you should instead use the `setValueAs` method and convert from string yourself. I wrote an example on how to have optional number inputs with react-hook-form and zod [on GitHub](https://github.com/react-hook-form/react-hook-form/discussions/6980#discussioncomment-1785009).

## Example of FormField component

If you want an example on how the FormField component can look like here it is! ❤

{% gist 00c8164c3af1e649a2b70690a39d0da2 %}

[^1]: Of course one could allow the custom component to receive `any` props but I don't like that since one loses the type safety on the props.

---
Last updated December 17, 2021

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
