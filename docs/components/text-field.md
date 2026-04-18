# TextField

A text field is an input field that merchants can type into. It has a range of options and supports several text formats including numbers.

## Best practices

Text fields should:

- Be clearly labelled so it's obvious to the merchant what they should enter into the field.
- Be accurately labelled in a way that shows what kind of input is needed.
- Only ask for information that's really needed.
- Validate input as soon as merchants have finished interacting with a field (but not before).

## Content guidelines

For text fields, field labels should:

- Work in a range of contexts.
- Be concise but clear enough that the input is understood.
- Be written in sentence case (first word capitalised, rest lowercase).
- Not end in punctuation.

Help text should:

- Not be a rewording of the label.
- Be used to provide supplemental context to the label.
- Be written in sentence case.

Error messages should:

- Be clearly written so the merchant understands the error.
- Tell the merchant what they should do to fix the problem.

## Examples

### Basic text field

Use to allow merchants to enter a value.

```html
<p-text-field
  label="Product title"
  placeholder="Short sleeve T-shirt"
></p-text-field>
```

### With help text

Use to convey information about what to enter in the text field.

```html
<p-text-field
  label="Email"
  type="email"
  help-text="We'll use this address to send order confirmations."
></p-text-field>
```

### With error

Use to let merchants know if their input is invalid so they can fix it.

```html
<p-text-field
  label="Price"
  type="number"
  value="-5"
  error="Price must be greater than zero."
></p-text-field>
```

### Multiline

Use when the expected input is more than one line of text.

```html
<p-text-field
  label="Description"
  multiline
  placeholder="Describe your product in detail…"
></p-text-field>
```

### With prefix and suffix

Use when a currency symbol or unit of measure is needed.

```html
<p-text-field
  label="Price"
  type="number"
  prefix="£"
></p-text-field>

<p-text-field
  label="Weight"
  type="number"
  suffix="kg"
></p-text-field>
```

### Character count

Use to help merchants understand how much text they can enter.

```html
<p-text-field
  label="Short description"
  max-length="200"
  show-character-count
></p-text-field>
```

### Disabled

Use to show that a field exists, but isn't currently available.

```html
<p-text-field
  label="Store URL"
  value="my-store.myshopify.com"
  disabled
></p-text-field>
```

### Read-only

Use when merchants need to be able to copy the value but shouldn't change it.

```html
<p-text-field
  label="API key"
  value="sk_live_abc123xyz"
  read-only
></p-text-field>
```

## Props

| Prop               | Type    | Default   | Description |
|--------------------|---------|-----------|-------------|
| `label`            | string  | —         | Visible label above the field. **Required.** |
| `value`            | string  | `""`      | Current value of the field. |
| `type`             | string  | `"text"`  | HTML input type. Options: `"text"`, `"number"`, `"email"`, `"password"`, `"search"`, `"tel"`, `"url"`. |
| `placeholder`      | string  | —         | Hint text displayed when the field is empty. |
| `help-text`        | string  | —         | Descriptive text below the label. |
| `error`            | string  | —         | Error message; puts field in error state. |
| `prefix`           | string  | —         | Text or symbol shown before the input value. |
| `suffix`           | string  | —         | Text or symbol shown after the input value. |
| `disabled`         | boolean | `false`   | Prevents interaction. |
| `read-only`        | boolean | `false`   | Value readable but not editable. |
| `multiline`        | boolean | `false`   | Renders a `<textarea>` instead of `<input>`. |
| `rows`             | number  | `4`       | Number of visible text rows when `multiline` is true. |
| `auto-complete`    | string  | —         | Maps to the HTML `autocomplete` attribute. |
| `max-length`       | number  | —         | Maximum number of characters allowed. |
| `show-character-count` | boolean | `false` | Displays a character counter. |
| `clear-button`     | boolean | `false`   | Adds a clear button at the right of the field. |
| `label-hidden`     | boolean | `false`   | Visually hides the label (kept for screen readers). |
| `focused`          | boolean | `false`   | Forces the field into focus state. |

## Events

| Event        | Description |
|--------------|-------------|
| `p-change`   | Fires when the value changes. Detail: `{ value: string }`. |
| `p-input`    | Fires on every keystroke. Detail: `{ value: string }`. |
| `p-focus`    | Fires when the field receives focus. |
| `p-blur`     | Fires when the field loses focus. |
| `p-clear`    | Fires when the clear button is clicked (requires `clear-button`). |

## Accessibility

- Always provide a `label` — it is used as the accessible name for the input.
- Use `help-text` for supplemental context rather than relying on placeholder text, which disappears once typing begins.
- Error messages are announced to screen readers via `aria-describedby`.
- The `label-hidden` attribute visually hides the label while keeping it in the accessibility tree.
