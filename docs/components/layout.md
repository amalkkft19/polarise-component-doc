# Layout

Use the layout component to create the main layout of a page. Layouts sections come in three main configurations: one-column, two-column, and annotated.

## Best practices

Layouts should:

- Use the annotated layout for settings pages where explanations are needed.
- Use the two-column layout for comparing information side by side.
- Not be nested inside one another.

## Content guidelines

Annotated section titles should:

- Be clear and concise.
- Not end in punctuation.

Annotated section descriptions should:

- Explain *why* the section exists, not just what it contains.

## Examples

### One-column layout

Use for simple, linear content.

```html
<p-layout>
  <p-layout-section>
    <p-card title="Products" sectioned>
      <p>Manage your product catalogue.</p>
    </p-card>
  </p-layout-section>
</p-layout>
```

### Two-column layout (one-half)

Use to display related information side by side.

```html
<p-layout>
  <p-layout-section one-half>
    <p-card title="Revenue" sectioned>
      <p>£12,300 this month</p>
    </p-card>
  </p-layout-section>

  <p-layout-section one-half>
    <p-card title="Orders" sectioned>
      <p>342 orders this month</p>
    </p-card>
  </p-layout-section>
</p-layout>
```

### Three-column layout (one-third)

```html
<p-layout>
  <p-layout-section one-third>
    <p-card title="Total sales" sectioned>
      <p>£12,300</p>
    </p-card>
  </p-layout-section>

  <p-layout-section one-third>
    <p-card title="Orders" sectioned>
      <p>342</p>
    </p-card>
  </p-layout-section>

  <p-layout-section one-third>
    <p-card title="Visitors" sectioned>
      <p>5,200</p>
    </p-card>
  </p-layout-section>
</p-layout>
```

### Primary/secondary (two-thirds / one-third)

Use for a main content area with a sidebar.

```html
<p-layout>
  <p-layout-section>
    <p-card title="Product information" sectioned>
      <!-- main content -->
    </p-card>
  </p-layout-section>

  <p-layout-section secondary>
    <p-card title="Visibility" sectioned>
      <!-- sidebar content -->
    </p-card>
    <p-card title="Tags" sectioned>
      <!-- sidebar content -->
    </p-card>
  </p-layout-section>
</p-layout>
```

### Annotated layout

Use for settings pages to explain what each section does.

```html
<p-layout>
  <p-layout-annotated-section
    title="Store details"
    description="Shopify and your customers will use this information to contact you."
  >
    <p-card sectioned>
      <p-text-field label="Store name"></p-text-field>
      <p-text-field label="Store email" type="email"></p-text-field>
    </p-card>
  </p-layout-annotated-section>

  <p-layout-annotated-section
    title="Billing address"
    description="Your billing address is used for invoices sent by Shopify."
  >
    <p-card sectioned>
      <p-text-field label="Address line 1"></p-text-field>
      <p-text-field label="City"></p-text-field>
      <p-select label="Country" options="[...]"></p-select>
    </p-card>
  </p-layout-annotated-section>
</p-layout>
```

## LayoutSection props

| Prop        | Type    | Default | Description |
|-------------|---------|---------|-------------|
| `one-half`  | boolean | `false` | Section takes half the row width. |
| `one-third` | boolean | `false` | Section takes a third of the row width. |
| `secondary` | boolean | `false` | Section acts as a sidebar (one-third width, right side). |
| `full-width`| boolean | `false` | Section spans full width even inside a multi-column layout. |

## LayoutAnnotatedSection props

| Prop          | Type   | Default | Description |
|---------------|--------|---------|-------------|
| `title`       | string | —       | Section heading displayed on the left. |
| `description` | string | —       | Explanatory text below the title. |

## Accessibility

- Layout does not add any ARIA roles — it is purely structural.
- Ensure the reading order of sections makes sense in document order (top to bottom, left to right), as screen readers follow source order.
