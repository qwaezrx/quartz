---
tags:
  - CS/Programming/Language/HTML
---


### `<input>`
Used to create interactive controls.

The key attribute of this element is `type`. Some common values for `type` include:
- `button`
- `checkbox`
- `date`
- `email`
- `number`
- `password`
- `submit`
- `text`
- `url`
These values dictate the appearance of the element. For example:
```html
<form action="my_action_page">
	<label for="uname">Username:</label>
	<br>
	<input type="text" id="uname" name="username">
	<br>
	<label for="pwd">Password:</label>
	<br>
	<!-- "password" hides the user input -->
	<input type="password" id="pwd" name="pwd">
	<br><br>
	<input type="submit" value="Login">
</form>
```

<form action="my_action_page">
	<label for="uname">Username:</label>
	<br>
	<input type="text" id="uname" name="username">
	<br>
	<label for="pwd">Password:</label>
	<br>
	<!-- "password" hides the user input -->
	<input type="password" id="pwd" name="pwd">
	<br><br>
	<input type="submit" value="Login">
</form>

---
### `<label>`
Defines a label for an element. It has an attribute __"for"__, the value of which should be equal to the __"id"__ attribute of the element it is associated with.

---
### `<select>`
Defines a drop-down list of options presented to the user. It has couple of attributes:
- __Form__: The id of the form in which the drop-down appears
- __Name__
- __Multiple Boolean__: When specified, indicates if a user can select multiple options
- __Required__
- __Size__: Mentions the number of visible options in a drop-down list
The options in a drop-down list are defined using the `<option>` element inside `<select>`.

---
### `<textarea>`
Defines a multi-line input field.
The common attributes for this element include:
- `cols`: Defines the width of the text area, default is 20
- `form`: Form element the text area is associated with
- `maxlength`
- `minlength`
- `readonly`
- `rows`: Defines the number of visible text lines for the text area
```html
<textarea name="response" rows="10" cols="30" maxlength="200">
</textarea>
```

<textarea name="response" rows="10" cols="30" maxlength="200"></textarea>

---
### `<button>`
Defines a clickable button. The `onclick` attribute defines the behavior when the button is clicked by the user.
```html
<button type="button" onclick="alert('You just clicked!')">Click me!
</button>
```

<button type="button" onclick="alert('You just clicked!')">Click me!</button>

---
### `<fieldset>`
Used to group related input elements in a form. For instance, elements related to the user's personal information and educational qualification can be grouped separately in two field sets.

---
### `<legend>`
Defines a caption for the `<fieldset>` element. For example:
```html
<fieldset>
	<legend>Personal Info</legend>
	<label for="fname">First Name:</label><br>
	<input type="text" id="fname" name="fname" value="John"><br>
	<label for="lname">Last Name:</label><br>
	<input type="text" id="lname" name="lname" value="Doe"><br>
</fieldset>
<fieldset>
	<legend>Qualification</legend>
</fieldset>
```

<fieldset>
	<legend>Personal Info</legend>
	<label for="fname">First Name:</label><br>
	<input type="text" id="fname" name="fname" value="John"><br>
	<label for="lname">Last Name:</label><br>
	<input type="text" id="lname" name="lname" value="Doe"><br>
</fieldset>
<fieldset>
	<legend>Qualification</legend>
	<label for="pdegree">Primary Degree:</label><br>
	<input type="text" id="pdegree" name="degree" value="Masters"><br>
</fieldset>

---
### `<datalist>`
Specifies a list of pre-defined options for an input  element. It differs from `<select>` since the user can still provide textual or numeric input other than the listed options.
```html
<form action="/my_action_page">
	<label for="flowers">Favorite Flowers:</label>
	<input list="flowers" name="flowers">
	<datalist id="flowers">
		<option value="Rose">
		<option value="Lily">
		<option value="Tulip">
		<option value="Daffodil">
	</datalist>
</form>
```

<form action="/my_action_page">
	<label for="flowers">Favorite Flowers:</label>
	<input list="flowers" name="flowers">
	<datalist id="flowers">
		<option value="Rose">
		<option value="Lily">
		<option value="Tulip">
		<option value="Daffodil">
	</datalist>
	...
</form>

---
### `<output>`
Represents the result of a calculation (typically the output of a script) or the outcome of the user action.

---
### `<option>`
Defines an option for the drop-down list.
```html
<label for="course">Choose a course:</label><br>
<select id="course" name="courselist">
	<option value="html">HTML Introduction</option>
	<option value="css">Styling with CSS</option>
	<option value="js">JavaScript</option>
	<option value="react">React Basics</option>
</select>
<!-- By default, the first item in the drop-down list is selected -->
```


<label for="course">Choose a course:</label><br>
<select id="course" name="courselist">
	<option value="html">HTML Introduction</option>
	<option value="css">Styling with CSS</option>
	<option value="js">JavaScript</option>
	<option value="react">React Basics</option>
</select>

---
### `<optgroup>`
Defines a group of related options in a drop-down list. Its attribute label names the group.

---
