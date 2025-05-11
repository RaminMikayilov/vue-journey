# Interpolation

## 🧠 What is Interpolation?

Interpolation in Vue is used to insert dynamic values into the DOM. This can be plain text, or JavaScript expressions evaluated in the context of Vue's reactivity system.

### Syntax:

```html
{{ expression }}
```

# Directives

## 🧠 What are Directives?

Directives are special tokens in the markup that tell the library to do something to a DOM element. They are prefixed with `v-` to indicate that they are special attributes provided by Vue.

### Common Directives:

- `v-bind`: Dynamically bind one or more attributes, or a component prop to an expression.
- `v-model`: Create two-way data bindings on form input, textarea, and select elements.
- `v-if`: Conditionally render elements based on a boolean expression.
- `v-else`: Render an element if the previous `v-if` or `v-else-if` condition is false.
- `v-else-if`: Add an else-if condition to a previous `v-if`.
- `v-show`: Toggle the visibility of an element based on a boolean expression.
- `v-for`: Render a list of items by iterating over an array or object.
- `v-on`: Attach event listeners to elements.
- `v-slot`: Define a slot for a component.
