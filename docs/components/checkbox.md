# Checkbox

Checkboxes are most commonly used to give merchants a way to make a range of selections (zero, one, or multiple). They may also be used as a way to have merchants indicate they've read and accepted terms.

## Best practices

Checkboxes should:

- Work independently from each other: selecting one checkbox shouldn't change the selection status of another checkbox in the list (unless the checkbox is a "select all" type).
- Be framed positively: "opt in to" rather than "opt out of".
- Always have a label when used to activate or deactivate a setting.
- Be listed vertically when grouping multiple checkboxes.

## Content guidelines

Checkbox labels should:

- Start with a capital letter.
- Not end in punctuation if they're part of a list.
- Be written so that selecting the checkbox is clearly understood as a positive action.

## Examples

### Basic checkbox

```html
<p-checkbox label="Publish to online store"></p-checkbox>
```

### Checked by default

```html
<p-checkbox label="Subscribe to marketing emails" checked></p-checkbox>
```

### Indeterminate

Use the indeterminate state for "select all" controls when only some child items are selected.

```html
<p-checkbox
  label="Select all products"
  indeterminate
  id="select-all"
></p-checkbox>
```

### With help text

```html
<p-checkbox
  label="Notify customers by email"
  help-text="An automatic email will be sent when the order is fulfilled."
></p-checkbox>
```

### With error

```html
<p-checkbox
  label="I agree to the terms and conditions"
  error="You must accept the terms and conditions to continue."
></p-checkbox>
```

### Disabled

```html
<p-checkbox label="Enable two-step authentication" disabled></p-checkbox>
```

## Props

| Prop            | Type    | Default | Description |
|-----------------|---------|---------|-------------|
| `label`         | string  | —       | Visible label. **Required.** |
| `checked`       | boolean | `false` | Whether the checkbox is checked. |
| `indeterminate` | boolean | `false` | Shows a mixed (indeterminate) state. |
| `help-text`     | string  | —       | Descriptive text below the checkbox. |
| `error`         | string  | —       | Error message. |
| `disabled`      | boolean | `false` | Prevents interaction. |
| `name`          | string  | —       | Name attribute for form submission. |
| `value`         | string  | —       | Value submitted with a form. |
| `label-hidden`  | boolean | `false` | Visually hides the label (kept for screen readers). |

## Events

| Event      | Description |
|------------|-------------|
| `p-change` | Fires when the checked state changes. Detail: `{ checked: boolean }`. |

## Accessibility

- Uses a native `<input type="checkbox">` element for full browser and AT compatibility.
- The `label` attribute is associated with the input via `<label for="...">`.
- `indeterminate` sets the `indeterminate` DOM property and `aria-checked="mixed"`.
- Error messages are linked via `aria-describedby`.
