---
tags:
  - CS
---

Offer a declarative application programming interface to enable full control of the state of form elements at any point in time using React state.

---
When comes to React applications, [[HTML]] forms work differently to other [[DOM]] elements.

Rather than relying on the native state of the DOM elements, the React state is made the single source of truth. Controlling the displayed value of your form elements at all times.

The way you perform this state delegation is via the value prop.

> ### Value
> A special property to determine input content that React added to most of the form elements 

In order to create a controlled component, you need to use a combination of local state and the value prop.
Initially, you will assign the local state to the value property.

> ### onChange callback
> Receives an event parameter, which is an event object representing the action that just took place.

```javascript
handleChange(event) {
    setValue(event.target.value);
}
```

> ### onSubmit callback

```html
<form onSubmit={handleSubmit}>
   -
</form>

handleSubmit(event) {
    validate(value);
    event.preventDefault();
}
```

## Summary
Controlled components enables React to be the source of truth for the state of the form inputs. React offers controlled versions of the majority of input types and recommend using controlled components for the implementation of forums.
However, there is still some form elements that remain uncontrolled similar to the native HTML DOM counterparts.