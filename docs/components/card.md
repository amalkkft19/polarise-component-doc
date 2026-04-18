# Card

Cards are used to group similar concepts and tasks together to make Shopify easier for merchants to scan, read, and get things done.

## Best practices

Cards should:

- Use headings that set clear expectations about the card's purpose.
- Prioritise information so the content merchants most need to see is first.
- Stick to single topics or a set of closely related topics.
- Avoid too much detail in a single card — use multiple cards or a modal if needed.
- Use sections to further organise content within a card.

## Examples

### Basic card

```html
<p-card title="Online store dashboard" sectioned>
  <p>View a summary of your online store's performance.</p>
</p-card>
```

### With sections

Use sections to separate distinct groups of content within a card.

```html
<p-card title="Product availability">
  <p-card-section>
    <p>This product is available on these channels.</p>
    <!-- channel list -->
  </p-card-section>

  <p-card-section title="Sales channels">
    <!-- sales channel content -->
  </p-card-section>
</p-card>
```

### With primary action

Use to provide a main action for the card's content.

```html
<p-card
  title="Products"
  primary-action-content="Add product"
  primary-action-url="/products/new"
>
  <p>You currently have 42 products.</p>
</p-card>
```

### With secondary actions

```html
<p-card
  title="Shipping settings"
  primary-action-content="Manage"
  secondary-actions='[
    { "content": "Duplicate", "url": "/shipping/duplicate" },
    { "content": "Archive",   "url": "/shipping/archive"   }
  ]'
>
  <p>Shipping rates and methods for your store.</p>
</p-card>
```

### Subdued card

Use a subdued card for content that is less important than the surrounding content.

```html
<p-card title="Archived orders" subdued sectioned>
  <p>These orders have been archived and are read-only.</p>
</p-card>
```

## Props

| Prop                     | Type    | Default | Description |
|--------------------------|---------|---------|-------------|
| `title`                  | string  | —       | Heading of the card. |
| `sectioned`              | boolean | `false` | Wraps children in a `<p-card-section>` automatically. |
| `subdued`                | boolean | `false` | Applies a subdued background colour. |
| `primary-action-content` | string  | —       | Label for the header primary action. |
| `primary-action-url`     | string  | —       | URL for the header primary action. |
| `secondary-actions`      | JSON    | —       | Array of `{ content, url, onAction? }` objects for additional actions. |

## Slots

| Slot        | Description |
|-------------|-------------|
| *(default)* | Card body content. |
| `actions`   | Custom action area in the header. |
| `footer`    | Content pinned to the bottom of the card. |

## CardSection props

`<p-card-section>` can be used as a direct child of `<p-card>` to create distinct sections.

| Prop       | Type    | Default | Description |
|------------|---------|---------|-------------|
| `title`    | string  | —       | Section heading. |
| `subdued`  | boolean | `false` | Applies a subdued background colour to the section. |
| `flush`    | boolean | `false` | Removes section padding. |
| `hidden-when-empty` | boolean | `false` | Hides the section when it has no content. |

## Accessibility

- Card headings are rendered as `<h2>` elements by default, following document outline best practices.
- Ensure the reading order of content within a card follows a logical sequence.
