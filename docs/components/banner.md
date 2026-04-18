# Banner

Banners are used to inform merchants about important changes or persistent conditions. Use a banner to communicate a message that the merchant needs to see clearly.

## Best practices

Banners should:

- Be used sparingly — multiple banners on a screen reduce the urgency of each one.
- Be placed at the top of the page or section they relate to.
- Be dismissible whenever possible, so merchants can remove them once read.
- Clearly explain the nature of the problem and what merchants can do to resolve it.

## Content guidelines

### Title

- Use a noun or noun phrase: "Payment failed", "Your trial has ended".
- Don't start with "Error", "Warning", or "Note" — the icon communicates the status.

### Body text

- Explain clearly what the issue is and what the merchant should do.
- Use one sentence per idea.
- Don't use jargon.

### Actions

- Primary actions should resolve the issue described in the banner.
- Secondary actions provide an alternative or a path to learn more.

## Examples

### Informational banner

Use to inform merchants about something relevant that doesn't need immediate attention.

```html
<p-banner title="Before you add a product" status="info">
  <p>
    Your store doesn't have the Shipping app installed. 
    <a href="/apps/shipping">Install Shipping</a> before adding a product.
  </p>
</p-banner>
```

### Success banner

Use to inform merchants that something has gone right.

```html
<p-banner
  title="Shipment label created"
  status="success"
  dismissible
>
  Your shipping label for Order #1001 has been created and is ready to download.
</p-banner>
```

### Warning banner

Use to tell merchants about something that needs attention, but that doesn't prevent them from continuing.

```html
<p-banner
  title="Some of your products are unavailable"
  status="warning"
  action-content="View products"
  action-url="/products?status=unavailable"
  dismissible
>
  5 products are not available because they have 0 inventory. 
  Update your inventory to make them available.
</p-banner>
```

### Critical banner

Use to tell merchants about something critical that requires immediate action.

```html
<p-banner
  title="Your payment was declined"
  status="critical"
  action-content="Update payment method"
  action-url="/billing"
>
  Your most recent payment was declined. Add a new payment method 
  to continue using Shopify.
</p-banner>
```

### Dismissible banner

Use when the information is not critical and merchants may want to dismiss it.

```html
<p-banner
  title="New feature available"
  status="info"
  dismissible
  id="feature-banner"
>
  You can now bulk edit product variants from the product list.
</p-banner>

<script>
  document.getElementById('feature-banner')
    .addEventListener('p-dismiss', (e) => {
      e.target.remove();
    });
</script>
```

## Props

| Prop                       | Type    | Default | Description |
|----------------------------|---------|---------|-------------|
| `title`                    | string  | —       | Banner heading. |
| `status`                   | string  | —       | Visual style. Options: `"success"`, `"info"`, `"warning"`, `"critical"`. |
| `action-content`           | string  | —       | Label for the primary action button. |
| `action-url`               | string  | —       | URL for the primary action (renders a link). |
| `secondary-action-content` | string  | —       | Label for the secondary action. |
| `secondary-action-url`     | string  | —       | URL for the secondary action. |
| `dismissible`              | boolean | `false` | Shows a dismiss button on the right side. |
| `stop-animations`          | boolean | `false` | Disables the entry animation (useful for testing). |

## Events

| Event         | Description |
|---------------|-------------|
| `p-action`    | Fires when the primary action is clicked. |
| `p-dismiss`   | Fires when the dismiss button is clicked. |
| `p-secondary-action` | Fires when the secondary action is clicked. |

## Slots

| Slot        | Description |
|-------------|-------------|
| *(default)* | Banner body content. Can include HTML such as links and lists. |

## Accessibility

- Banners use `role="alert"` for critical and warning statuses, triggering immediate announcement to screen readers.
- Informational and success banners use `role="status"` (polite announcement).
- The `title` is rendered as a heading inside the banner for document structure.
- When a banner is removed from the DOM, ensure focus is returned to a logical element.
