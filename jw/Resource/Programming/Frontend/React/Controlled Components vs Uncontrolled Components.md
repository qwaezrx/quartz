## Introduction
Since React recommends to use controlled components over uncontrolled components, it is important to understand the difference between the two.

## Uncontrolled Inputs
Uncontrolled inputs are similar to traditional HTML form inputs.
```jsx
const Form = () => {
    return (
        <div>
            <input type="text" />
        </div>
    );
};
```
The DOM itself maintains the internal state of the input.

How can we get their value? By using React ref.
```jsx
const From = () => {
    const inputRef = useRef(null);

    const handleSubmit = () => {
        const inputValue = inputRef.current.value;
        // Do something with the value
    }
    return (
        <form onSubmit={handleSubmit}>
            <input ref={inputRef} type="text" />
        </form>
    );
};
```
In other words, you must __pull__ the value from the field when needed.

## Controlled Inputs
Contolled inputs accept their current value as a prop and a callback to change that value. This means that the value of the input has to live in the React state somewhere. The component that renders the input saves that in its state.
```jsx
const Form = () => {
    const [value, setValue] = useState("");

    const handleChange = (e) => {
        setValue(e.target.value);
    }
    return (
        <form>
            <input
                value={value}
                onChange={handleChange}
                type="text"
            />
        </form>
    );
};
```
Every time you type a character, the `handleChange` function is executed.
This flow __pushes__ the value changes to the form component instead of pulling like the ref example from the uncontrolled version. Therefore, the Form component always has the input's current value without needing to ask for it explicitly.

## The file input type
There are some input types that are always uncontrolled, like the file input tag.

In React, an `<input type="file" />` is always an uncontrolled component because its value is read-only and can't be set programmatically.

The following example is how to create a ref to the DOM node to access any files selected in the form submit handler:
```jsx
const Form = () => {
    const fileInput = useRef(null);

    const handleSubmit = (e) => {
        e.preventDefault();
        const files = fileInput.current.files;
        // Do something with the files
    }
    return (
        <form onSubmit={handleSubmit}>
            <input
                ref={fileInput}
                type="file"
            />
        <form>
    );
};
```

## Summary

| Feature | Controlled | Uncontrolled |
|:--------|:----------:|:------------:|
| One-time value retrieval (e.g. on submit)      | ✅ | ✅ |
| Validating on submit                           | ✅ | ✅ |
| Instant field validation                       | ✅ | ❌ |
| Conditionally disabling submit button          | ✅ | ❌ |
| Enforcing specific formats (e.g. phone number) | ✅ | ❌ |
| Several inputs for one piece of data           | ✅ | ❌ |
| Dynamic inputs                                 | ✅ | ❌ |