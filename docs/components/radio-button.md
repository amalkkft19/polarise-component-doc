# RadioButton

Radio buttons are used to present each item in a list of options where merchants must make a single selection.

## Best practices

Radio buttons should:

- Always be used in a group of two or more options.
- Be mutually exclusive within a group — selecting one deselects the others.
- Include a group label that describes what the options are about.
- List options vertically when possible, for easier scanning.

For binary choices (yes/no, on/off), prefer a checkbox or toggle.

## Content guidelines

Radio button labels should:

- Start with a capital letter.
- Not end in punctuation.
- Clearly distinguish each option from the others.
- Be brief — ideally one or two words, or a short phrase.

## Examples

### Basic radio buttons

Group radio buttons using the `name` attribute.

```html
<p-radio-button
  label="Standard shipping — Free"
  name="shipping"
  value="standard"
  checked
></p-radio-button>

<p-radio-button
  label="Express shipping — £9.99"
  name="shipping"
  value="express"
></p-radio-button>

<p-radio-button
  label="Next-day shipping — £19.99"
  name="shipping"
  value="next-day"
></p-radio-button>
```

### With help text

```html
<p-radio-button
  label="Authorize only"
  name="payment-capture"
  value="authorize"
  help-text="Payment will be captured when you fulfil the order."
></p-radio-button>

<p-radio-button
  label="Authorize and capture"
  name="payment-capture"
  value="capture"
  help-text="Payment will be captured immediately when the order is placed."
></p-radio-button>
```

### Disabled option

```html
<p-radio-button
  label="Same-day delivery"
  name="shipping"
  value="same-day"
  help-text="Not available in your region."
  disabled
></p-radio-button>
```

## Props

| Prop        | Type    | Default | Description |
|-------------|---------|---------|-------------|
| `label`     | string  | —       | Visible label. **Required.** |
| `name`      | string  | —       | Groups related radio buttons. **Required.** |
| `value`     | string  | —       | Value submitted with a form. |
| `checked`   | boolean | `false` | Whether this option is selected. |
| `help-text` | string  | —       | Descriptive text below the radio button. |
| `disabled`  | boolean | `false` | Prevents interaction. |

## Events

| Event      | Description |
|------------|-------------|
| `p-change` | Fires when this radio button becomes selected. Detail: `{ value: string }`. |

## Accessibility

- Uses a native `<input type="radio">` element.
- All radio buttons sharing the same `name` attribute form a radio group accessible by keyboard arrow keys.
- The group should be wrapped in a `<fieldset>` with a `<legend>` when used in a form for full accessibility compliance.

```html
<fieldset>
  <legend>Shipping method</legend>

  <p-radio-button label="Standard — Free"   name="shipping" value="standard" checked></p-radio-button>
  <p-radio-button label="Express — £9.99"   name="shipping" value="express"></p-radio-button>
</fieldset>
```
