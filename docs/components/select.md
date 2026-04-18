# Select

Select lets merchants choose one option from an options menu. Consider select when you have 4 or more options, to avoid overwhelming merchants with too many choices.

## Best practices

The select component should:

- Be used for selecting between 4 or more pre-defined options.
- Always be accompanied by a label.
- Not be used to navigate merchants to a different part of the product — use a link instead.
- Not be used to trigger actions — use a button instead.

For fewer than 4 options, consider using radio buttons so all choices are visible at once.

## Content guidelines

The select component's label should:

- Be written in sentence case.
- Not end in punctuation.
- Clearly indicate what the merchant is choosing.

Option labels should:

- Be distinct from one another.
- Start with a capital letter.
- Not be long descriptions — keep them short and scannable.

## Examples

### Basic select

Use the select to let merchants choose from a list of options.

```html
<p-select
  label="Country"
  options='[
    { "label": "Australia",      "value": "AU" },
    { "label": "Canada",         "value": "CA" },
    { "label": "Ireland",        "value": "IE" },
    { "label": "United Kingdom", "value": "GB" },
    { "label": "United States",  "value": "US" }
  ]'
  value="GB"
></p-select>
```

### With help text

Use to provide additional context about the available options.

```html
<p-select
  label="Currency"
  help-text="Prices in your store are shown in this currency."
  options='[
    { "label": "US Dollar (USD)", "value": "USD" },
    { "label": "Euro (EUR)",      "value": "EUR" },
    { "label": "British Pound (GBP)", "value": "GBP" }
  ]'
></p-select>
```

### With error

Use to indicate that the current selection is invalid.

```html
<p-select
  label="Shipping zone"
  error="Please select a shipping zone."
  options='[
    { "label": "Select a zone", "value": "", "disabled": true },
    { "label": "Europe",        "value": "EU" },
    { "label": "North America", "value": "NA" },
    { "label": "Asia Pacific",  "value": "AP" }
  ]'
></p-select>
```

### Disabled

Use to show that the field exists but isn't currently available.

```html
<p-select
  label="Language"
  value="en"
  disabled
  options='[
    { "label": "English", "value": "en" },
    { "label": "French",  "value": "fr" }
  ]'
></p-select>
```

### With option groups

Use to organise a long list of options into logical sections.

```html
<p-select
  label="Font"
  option-groups='[
    {
      "title": "Serif",
      "options": [
        { "label": "Georgia",     "value": "georgia" },
        { "label": "Times New Roman", "value": "times" }
      ]
    },
    {
      "title": "Sans-serif",
      "options": [
        { "label": "Arial",       "value": "arial" },
        { "label": "Helvetica",   "value": "helvetica" }
      ]
    }
  ]'
></p-select>
```

## Props

| Prop            | Type    | Default | Description |
|-----------------|---------|---------|-------------|
| `label`         | string  | —       | Visible label. **Required.** |
| `options`       | JSON    | `[]`    | Array of `{ label, value, disabled? }` objects. |
| `option-groups` | JSON    | —       | Array of `{ title, options[] }` for grouped options. |
| `value`         | string  | —       | Currently selected value. |
| `help-text`     | string  | —       | Descriptive text below the select. |
| `error`         | string  | —       | Error message; puts the field in error state. |
| `disabled`      | boolean | `false` | Prevents interaction. |
| `label-hidden`  | boolean | `false` | Visually hides the label (kept for screen readers). |

## Events

| Event      | Description |
|------------|-------------|
| `p-change` | Fires when the selected value changes. Detail: `{ value: string }`. |

## Accessibility

- The `label` attribute is used as the accessible name for the `<select>` element.
- Error messages are associated via `aria-describedby` and announced to screen readers.
- Disabled options within the list are given `aria-disabled="true"`.
