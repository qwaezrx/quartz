### Required
Denotes a mandatory input that the user can't leave empty. It can be used with any input type.
```html
<input type="text" id="firstName" name="firstName" required>
```
### Maxlength
```html
<input type="text" id="description" name="description" maxlength="50">
```
### Minlength
```html
<input type="password" id="password" name="password" minlength="8">
```
### Min & Max attributes
Usually applied to numerical text inputs, range inputs or dates.
```html
<input type="number" id="quantity" name="quantity" min="1" max="100">
<input type="range" id="volume" name="volume" min="1" max="100">
```
### Multiple
Indicates that the user can enter more than one value in a single input field. This attribute can only be used for email file input types.
```html
<input type="file" id="gallery" name="gallery" multiple>
```
### Pattern
Defines a particular pattern that an input field value has to fulfill to be considered valid. This attribute expects a regular expression to specify the pattern. 
It works with:
- text
- date
- search
- URL
- tel
- email
- password
input types.
```html
<input type="tel" id="phone" name="phone" pattern="^(?:0|\+?44)(?:\d\s?){0,10}$">
```
