# Page

Use the page component to build the outer wrapper of a page, including the page title and associated actions.

## Best practices

The page component should:

- Always provide a title.
- Use a back action when the merchant has navigated deeper into the hierarchy.
- Include the most important action as the primary action.
- Not include more than one primary action.

## Content guidelines

### Title

- Should describe the current page content.
- Written in sentence case.
- Not end in punctuation.

### Back action

- Should describe where the merchant will go back to, not a generic "Back".
- Written in sentence case.

## Examples

### Basic page

```html
<p-page title="Products">
  <!-- page content -->
</p-page>
```

### Page with primary action

```html
<p-page title="Products">
  <p-button slot="primary-action" variant="primary" url="/products/new">
    Add product
  </p-button>

  <!-- page content -->
</p-page>
```

### Page with back action

```html
<p-page
  title="Edit product"
  back-action-content="Products"
  back-action-url="/products"
>
  <!-- page content -->
</p-page>
```

### Page with multiple actions

```html
<p-page
  title="Inventory"
  back-action-content="Products"
  back-action-url="/products"
>
  <p-button slot="primary-action" variant="primary">Save</p-button>

  <p-button slot="secondary-actions" url="/inventory/import">Import</p-button>
  <p-button slot="secondary-actions" url="/inventory/export">Export</p-button>
</p-page>
```

### Full-width page

Use when the content benefits from the full container width.

```html
<p-page title="Analytics" full-width>
  <!-- charts and graphs -->
</p-page>
```

### Narrow page

Use for focused tasks like editing a single item.

```html
<p-page
  title="Add discount code"
  narrow-width
  back-action-content="Discounts"
  back-action-url="/discounts"
>
  <!-- form -->
</p-page>
```

### Page with subtitle

```html
<p-page
  title="Short sleeve T-shirt"
  subtitle="Clothing > T-shirts"
  back-action-content="Products"
  back-action-url="/products"
>
  <!-- product form -->
</p-page>
```

## Props

| Prop                   | Type    | Default | Description |
|------------------------|---------|---------|-------------|
| `title`                | string  | —       | Page title. **Required.** |
| `subtitle`             | string  | —       | Optional subtitle below the title. |
| `back-action-content`  | string  | —       | Label for the back link. |
| `back-action-url`      | string  | —       | URL for the back link. |
| `full-width`           | boolean | `false` | Extends the page to full container width. |
| `narrow-width`         | boolean | `false` | Constrains the page to a narrower reading width. |
| `divider`              | boolean | `false` | Adds a divider line below the page header. |

## Slots

| Slot                 | Description |
|----------------------|-------------|
| *(default)*          | Page content. |
| `primary-action`     | Primary action element (button). |
| `secondary-actions`  | Secondary action elements. |
| `action-groups`      | Grouped overflow actions (for long action lists). |
| `additional-metadata` | Extra metadata below the page title. |
| `pagination`         | Pagination controls. |

## Accessibility

- The page title is rendered as an `<h1>` element.
- The back action is rendered as an anchor (`<a>`) element with a left-arrow icon.
- Ensure the page title accurately describes the current content for screen reader users who navigate by headings.
