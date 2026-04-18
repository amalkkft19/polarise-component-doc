# Tooltip

Tooltips are floating labels that briefly explain the function of a user interface element. They can be triggered when merchants hover over, focus on, or tap an element.

## Best practices

Tooltips should:

- Provide information that is not otherwise available or immediately obvious.
- Only be used on interactive elements, never on static text.
- Be brief — ideally less than a full sentence.
- Not contain interactive content such as links or buttons.
- Not be the only way to convey critical information.

## Content guidelines

Tooltip text should:

- Be concise and descriptive.
- Start with a capital letter.
- Not end with a period unless it's a complete sentence.
- Not repeat information that is already visible.

## Examples

### Basic tooltip

```html
<p-tooltip content="Print shipping label">
  <p-button icon="PrintMinor" variant="plain">Print</p-button>
</p-tooltip>
```

### Tooltip on a disabled button

Use to explain *why* a button is disabled.

```html
<p-tooltip content="Upgrade your plan to export CSV files">
  <p-button disabled>Export CSV</p-button>
</p-tooltip>
```

### Tooltip on an icon

```html
<p-tooltip content="Required field">
  <p-icon source="InfoMinor" color="subdued" accessibility-label="Information"></p-icon>
</p-tooltip>
```

### Positioned above the element

```html
<p-tooltip content="Opens in a new tab" preferred-position="above">
  <p-button url="https://shopify.com" external>Visit Shopify</p-button>
</p-tooltip>
```

### Always visible (for debugging/demos)

```html
<p-tooltip content="This tooltip is always visible" active>
  <p-button>Hover me</p-button>
</p-tooltip>
```

## Props

| Prop                 | Type    | Default    | Description |
|----------------------|---------|------------|-------------|
| `content`            | string  | —          | Tooltip text. **Required.** |
| `preferred-position` | string  | `"above"`  | Preferred placement. Options: `"above"`, `"below"`, `"mostSpace"`. |
| `active`             | boolean | `false`    | Forces the tooltip to always be visible. |
| `dismiss-on-mouse-out` | boolean | `false`  | Dismisses the tooltip as soon as the cursor leaves the trigger. |

## Slots

| Slot        | Description |
|-------------|-------------|
| *(default)* | The element the tooltip is attached to. |

## Accessibility

- Tooltip text is linked to its trigger element via `aria-describedby`.
- Tooltips are activated on hover AND focus, ensuring keyboard users can access the content.
- Do not put interactive elements inside a tooltip — it violates WCAG success criterion 1.4.13 (Content on Hover or Focus).
- Never use a tooltip as the sole means of conveying important information — it is invisible by default to touch-screen users.
