# Theming

You can easily extend or overwrite any part of Pollen by defining your own CSS variables in a `:root` pseudo-element. Pollen is designed to be a foundation for your own design system.

{% code title="variables.css" %}
```css
:root {
  --font-sans: 'Inter', sans-serif;
}
```
{% endcode %}

{% code title="app.js" %}
```javascript
import 'pollen-css';
import './variables.css';
```
{% endcode %}

### Globally Responsive

CSS variables can be changed inside media queries. And by redefining a variable on `:root` in a media query, that variable will be globally responsive.

```css
@media (max-width: 45em) {
  :root {
    --size-5: var(--size-4);
  }
}
```

### Javascript Interactivity

CSS variables are also accessed and updated in JavaScript, which allows you to accomplish things that were previously very complicated, like dynamically applying style themes. By updating a few key variables based on user input, you can reskin an entire interface.

Update CSS variables in JS by using the `setProperty` method on the document root’s style property.

```javascript
document.documentElement.style.setProperty(`--color-primary`, `#4299e1`);
```

You can also alias variables to other variables, this is useful for using a consistent property throughout your codebase that can be dynamically updated without losing meaning

```javascript
function enableDarkMode() {
  document.documentElement.style.setProperty(`--color-background`, `var(--color-black)`);
  document.documentElement.style.setProperty(`--color-text`, `white`)
}
```
