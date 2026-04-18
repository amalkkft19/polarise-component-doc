# Badge

Badges are used to inform merchants of the status of an object or of an action that's been taken.

## Best practices

Badges should:

- Use established status colours to quickly convey meaning at a glance.
- Be placed near the content they relate to.
- Not be used purely for decoration.
- Be used sparingly — too many badges create visual noise and reduce their impact.

## Content guidelines

Badge labels should:

- Be brief — ideally one or two words.
- Be written in sentence case (first word capitalised, rest lowercase).
- Clearly communicate the status they represent.

## Examples

### Default badge

```html
<p-badge>Draft</p-badge>
```

### Status badges

Use the `status` attribute to communicate meaning through colour.

```html
<p-badge status="success">Active</p-badge>
<p-badge status="info">Open</p-badge>
<p-badge status="attention">On hold</p-badge>
<p-badge status="warning">Pending</p-badge>
<p-badge status="critical">Payment failed</p-badge>
```

### Progress badges

Use `progress` to indicate partial completion alongside a status.

```html
<p-badge status="info" progress="incomplete">Unfulfilled</p-badge>
<p-badge status="warning" progress="partiallyComplete">Partially fulfilled</p-badge>
<p-badge status="success" progress="complete">Fulfilled</p-badge>
```

### Small badge

Use for compact UI areas where space is limited.

```html
<p-badge size="small" status="success">Active</p-badge>
```

## Props

| Prop       | Type   | Default    | Description |
|------------|--------|------------|-------------|
| `status`   | string | —          | Visual style and meaning. Options: `"success"`, `"info"`, `"attention"`, `"warning"`, `"critical"`. |
| `progress` | string | —          | Progress icon inside the badge. Options: `"incomplete"`, `"partiallyComplete"`, `"complete"`. |
| `size`     | string | `"medium"` | Size of the badge. Options: `"small"`, `"medium"`. |

## Accessibility

Badge content is read aloud by screen readers. When the status colour carries meaning, the text label must convey the same information so it is accessible without relying on colour alone.

For dynamic badge content that changes, wrap with an `aria-live` region:

```html
<span aria-live="polite">
  <p-badge id="status-badge" status="info">Processing</p-badge>
</span>

<script>
  // Later, when status changes:
  const badge = document.getElementById('status-badge');
  badge.status = 'success';
  badge.textContent = 'Complete';
</script>
```
