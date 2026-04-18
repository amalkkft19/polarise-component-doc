# Popover

Popovers are small overlays that open on demand. They let merchants access additional content and actions without cluttering the page.

## Best practices

Popovers should:

- Activate through a clear trigger (button or link).
- Be dismissed by clicking outside the popover or pressing Escape.
- Contain a small number of items — for long lists, use a modal instead.
- Be positioned to avoid overflowing the viewport.

## Content guidelines

- Keep content short and actionable.
- Use action lists inside popovers for groups of related actions.
- Use a `p-text-container` for brief explanatory text.

## Examples

### Basic popover with action list

```html
<p-popover id="actions-popover">
  <p-button slot="activator" disclosure>More actions</p-button>

  <p-action-list>
    <p-action-list-item url="/products/duplicate">Duplicate</p-action-list-item>
    <p-action-list-item url="/products/archive">Archive</p-action-list-item>
    <p-action-list-item destructive>Delete</p-action-list-item>
  </p-action-list>
</p-popover>

<script>
  const popover = document.getElementById('actions-popover');
  popover.querySelector('[slot="activator"]').addEventListener('click', () => {
    popover.active = !popover.active;
  });
  document.addEventListener('click', (e) => {
    if (!popover.contains(e.target)) popover.active = false;
  });
</script>
```

### Popover with form

Use to show a compact inline form.

```html
<p-popover id="date-popover">
  <p-button slot="activator">Select date</p-button>

  <div style="padding:1.6rem;">
    <p-text-field label="Start date" type="date"></p-text-field>
    <p-text-field label="End date" type="date"></p-text-field>
    <p-button variant="primary">Apply</p-button>
  </div>
</p-popover>
```

### Aligned to the right

```html
<p-popover preferred-alignment="right">
  <p-button slot="activator" disclosure>Sort</p-button>
  <!-- sort options -->
</p-popover>
```

### Full-width popover

Use when the popover should match the width of its activator.

```html
<p-popover full-width>
  <p-button slot="activator" full-width disclosure>Filter by status</p-button>
  <!-- filter options -->
</p-popover>
```

## Props

| Prop                   | Type    | Default    | Description |
|------------------------|---------|------------|-------------|
| `active`               | boolean | `false`    | Whether the popover is visible. |
| `preferred-alignment`  | string  | `"left"`   | Horizontal alignment. Options: `"left"`, `"right"`, `"center"`. |
| `preferred-position`   | string  | `"below"`  | Vertical position. Options: `"above"`, `"below"`, `"mostSpace"`. |
| `full-width`           | boolean | `false`    | Stretches the popover to match the activator width. |
| `prevent-close-on-child-overlay-click` | boolean | `false` | Keeps the popover open when a child modal is triggered. |

## Slots

| Slot        | Description |
|-------------|-------------|
| `activator` | The element that toggles the popover. |
| *(default)* | Popover body content. |

## Events

| Event     | Description |
|-----------|-------------|
| `p-close` | Fires when the popover is closed. |

## Accessibility

- The popover uses `aria-expanded` on the activator to communicate open/closed state.
- `role="dialog"` is set on the popover container.
- Press Escape to dismiss the popover; focus is returned to the activator.
- Ensure interactive elements inside the popover are keyboard-navigable in a logical order.
