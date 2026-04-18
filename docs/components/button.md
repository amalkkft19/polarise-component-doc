# Button

Buttons are used primarily for actions, such as "Add", "Close", "Cancel", or "Save". Plain buttons, which look similar to links, are used for less important or less commonly used actions, such as "view shipping settings".

## Best practices

Buttons should:

- Be clearly and accurately labelled.
- Lead with a strong, actionable verb.
- Use established button colours appropriately.
- Prioritise the most important action. To avoid overwhelming merchants, only use one primary button per section or screen.
- Never use a button to navigate to another place; use a link instead.
- Always have a fallback if JavaScript fails to load.

## Content guidelines

Buttons should be:

- Clear and predictable: merchants should be able to anticipate what will happen when they click a button.
- Action-led: buttons should always lead with a strong verb that encourages action.
- Scannable: avoid unnecessary words and articles such as "the", "an", or "a".

| ✅ Do        | ❌ Don't     |
|-------------|-------------|
| Add product | Add a product |
| Save changes | Submit form changes |
| Create order | New order |

## Examples

### Basic button

Use to most important actions.

```html
<p-button>Add product</p-button>
```

### Primary button

Use to highlight the most important action.

```html
<p-button variant="primary">Save changes</p-button>
```

### Destructive button

Use when the action will delete merchant data or be difficult to recover from.

```html
<p-button variant="destructive">Delete product</p-button>
```

### Plain button

Use for less prominent actions, or when other buttons overwhelm the interface.

```html
<p-button variant="plain">View details</p-button>
```

### Disabled state

Use for actions that aren't currently available. The surrounding interface should make it clear why the button is disabled and what merchants need to do to enable it.

```html
<p-button disabled>Save changes</p-button>
```

### Loading state

Use when a button action is in progress. The button is disabled while loading.

```html
<p-button loading>Saving…</p-button>
```

### Full-width button

Use for buttons that need to span the full width of their container.

```html
<p-button full-width variant="primary">Create order</p-button>
```

### Link button

Renders the button as an anchor tag.

```html
<p-button url="/orders">View all orders</p-button>
<p-button url="https://shopify.com" external>Visit Shopify</p-button>
```

## Props

| Prop        | Type    | Default     | Description |
|-------------|---------|-------------|-------------|
| `variant`   | string  | `"default"` | Changes the visual style. Options: `"primary"`, `"destructive"`, `"plain"`, `"monochrome"`. |
| `size`      | string  | `"medium"`  | Changes the size. Options: `"slim"`, `"medium"`, `"large"`. |
| `disabled`  | boolean | `false`     | Disables the button, preventing interaction. |
| `loading`   | boolean | `false`     | Replaces button content with a spinner. |
| `full-width`| boolean | `false`     | Makes the button fill its parent container. |
| `url`       | string  | —           | Renders the button as an anchor to this URL. |
| `external`  | boolean | `false`     | Opens the URL in a new tab. Only works with `url`. |
| `disclosure`| boolean | `false`     | Displays a chevron to indicate the button opens an overlay. |
| `icon`      | string  | —           | Name of an icon to display before the button text. |
| `icon-after`| boolean | `false`     | When set, renders the icon after the text rather than before. |

## Events

| Event   | Description |
|---------|-------------|
| `click` | Fired when the button is activated (unless `disabled` or `loading`). |

## Accessibility

- Buttons use a native `<button>` element (or `<a>` when `url` is set), ensuring keyboard and screen reader accessibility out of the box.
- Never remove the visible text label — screen readers and keyboard users rely on it.
- The `loading` state sets `aria-busy="true"` and announces "Loading" to screen readers.
- The `disabled` attribute sets `aria-disabled="true"` so screen readers can communicate the state.
