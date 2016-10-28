# KISS
Keep It Super Simple - Minimalist Javascript Framework

# Why?
This is a minimalistic framework : all you need is to know javascript. For less than 5kb, you can associate html templates to js functions easily, without any weird annotations nor complex architecture.

One HTML template + One Javscript File = One component.

# Getting Started
First, create `index.html`, which will be your main entry point in the application.
```html
<!doctype html>
<html>
	<body>
		{{component}}
		<script src="path/to/kiss.js"></script>
	</body>
</html>
```

Then, create `index.js` :
```javascript
// We associate the 'component' variable to the MyComponent, by passing the absolute path.
this.component = Kiss.component('./MyComponent');
```

Now, we can make our HTML part of the component `MyComponent.html`:
```html
<h1>{{foo}}</h1>
```

And its Javascript counterpart `MyComponent.js`:
```javscript
// We can associate the 'foo' variable to a string.
this.foo = 'Hello world!';
// And 'this' contains the reference to DOM component.
this.style.color = 'red';
```

Et voilà! This is super simple!

## References inside templates
You can also get reference of HTML elements inside templates:
```html
<div kiss:id="foo"></div>
```

```javascript
this.foo.innerHTML = 'bar';
```

## Default parameters
You can pass default parameters to components:
```javascript
Kiss.component('./MyComponent', {foo: 'bar'});
```

## Singletons
You may need to access singleton components, for creating services:

```javascript
var userService = Kiss.singleton('./UserService');
userService.dispatchEvent(new Event('my-event'));
```

```javascript 
var userService = Kiss.singleton('./UserService');
userService.addEventListener('my-event', ... );
```
