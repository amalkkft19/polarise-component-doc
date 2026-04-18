# Spinner

Spinners are used to notify merchants that their action is being processed. For loading states, spinners should only be used for content that can't be represented with skeleton content, such as rich text editors or comment sections.

## Best practices

Spinners should:

- Be used for loading states that take longer than ~300 ms.
- Always include an accessible label so screen reader users understand that content is loading.
- Be centred within their container when used as a page-level indicator.
- Be used inline (small size) when indicating loading within a button or a small content area.

## Content guidelines

The `accessibility-label` should:

- Describe what is loading: "Loading products", "Saving order".
- Not just say "Loading" if a more specific description is available.

## Examples

### Default spinner

Use for full-page or large-area loading states.

```html
<p-spinner accessibility-label="Loading product details"></p-spinner>
```

### Small spinner

Use inline with content or within a button.

```html
<p-spinner size="small" accessibility-label="Saving changes"></p-spinner>
```

### Centred spinner

Use a wrapper element to centre the spinner within a content area.

```html
<div style="display:flex; justify-content:center; padding:4rem 0;">
  <p-spinner accessibility-label="Loading orders"></p-spinner>
</div>
```

### Spinner inside a card

```html
<p-card sectioned>
  <div style="display:flex; justify-content:center;">
    <p-spinner accessibility-label="Loading analytics data"></p-spinner>
  </div>
</p-card>
```

## Props

| Prop                  | Type   | Default    | Description |
|-----------------------|--------|------------|-------------|
| `size`                | string | `"large"`  | Size of the spinner. Options: `"small"`, `"large"`. |
| `accessibility-label` | string | `"Loading"` | Text announced to screen readers. **Recommended.** |
| `has-focus-ring`      | boolean| `false`    | Shows a focus ring (used when the spinner replaces an interactive element). |

## Accessibility

- The spinner renders a visually hidden `<span>` containing the `accessibility-label` text.
- When a loading state begins, consider using `aria-live="polite"` on a parent container to announce changes to screen readers.
- When content finishes loading, move focus to the first interactive element or the main content heading.

```html
<!-- Announce loading state to screen readers -->
<div aria-live="polite" aria-atomic="true">
  <p-spinner accessibility-label="Loading your orders"></p-spinner>
</div>
```
