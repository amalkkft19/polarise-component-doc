# Shopify Polarise Web Components Documentation

A comprehensive documentation site for Shopify Polaris web components — the design system used to build Shopify's merchant-facing interfaces.

---

## Table of Contents

- [Overview](#overview)
- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Usage](#usage)
- [Components](#components)
  - [Actions](#actions)
    - [Button](#button)
  - [Forms](#forms)
    - [TextField](#textfield)
    - [Select](#select)
    - [Checkbox](#checkbox)
    - [RadioButton](#radiobutton)
  - [Feedback Indicators](#feedback-indicators)
    - [Badge](#badge)
    - [Banner](#banner)
    - [Spinner](#spinner)
  - [Structure](#structure)
    - [Card](#card)
    - [Page](#page)
    - [Layout](#layout)
  - [Overlays](#overlays)
    - [Modal](#modal)
    - [Popover](#popover)
    - [Tooltip](#tooltip)
  - [Images & Icons](#images--icons)
    - [Icon](#icon)
- [Theming & Customisation](#theming--customisation)
- [Accessibility](#accessibility)
- [Contributing](#contributing)
- [Licence](#licence)

---

## Overview

Shopify Polaris is Shopify's design system. It provides developers and designers with the tools to build high-quality, consistent experiences for Shopify merchants.

The **Polaris web components** (`@shopify/polaris`) are a set of framework-agnostic custom elements that implement the Polaris design language. They can be used in any web project regardless of the JavaScript framework (React, Vue, Angular, vanilla JS, etc.).

Key benefits:
- **Framework-agnostic** — use them in any environment that supports Custom Elements v1.
- **Accessible by default** — every component meets WCAG 2.1 AA standards.
- **Themeable** — CSS custom properties expose every design token.
- **Lightweight** — tree-shakeable ES modules; only pay for what you use.

---

## Getting Started

### Installation

Install the package from npm:

```bash
npm install @shopify/polaris
```

Or include the CDN bundle directly in your HTML:

```html
<link rel="stylesheet" href="https://unpkg.com/@shopify/polaris/build/esm/styles.css" />
<script type="module" src="https://unpkg.com/@shopify/polaris/build/esm/index.js"></script>
```

### Usage

Once installed, register the components and use them in your HTML:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Shopify App</title>
    <link rel="stylesheet" href="https://unpkg.com/@shopify/polaris/build/esm/styles.css" />
  </head>
  <body>
    <p-button variant="primary">Save changes</p-button>

    <script type="module">
      import '@shopify/polaris';
    </script>
  </body>
</html>
```

---

## Components

### Actions

#### Button

The `<p-button>` component triggers an action or navigates to a new location.

**Attributes**

| Attribute   | Type    | Default     | Description                                            |
|-------------|---------|-------------|--------------------------------------------------------|
| `variant`   | string  | `"default"` | Visual style: `"primary"`, `"destructive"`, `"plain"`, `"monochrome"`. |
| `size`      | string  | `"medium"`  | Size: `"slim"`, `"medium"`, `"large"`.                 |
| `disabled`  | boolean | `false`     | Prevents interaction.                                  |
| `loading`   | boolean | `false`     | Shows a loading spinner and disables the button.       |
| `full-width`| boolean | `false`     | Makes the button fill its container.                   |
| `url`       | string  | —           | If set, renders the button as an anchor element.       |
| `external`  | boolean | `false`     | Opens `url` in a new tab. Requires `url`.              |

**Events**

| Event    | Description              |
|----------|--------------------------|
| `click`  | Fired when button is clicked (unless `disabled` or `loading`). |

**Examples**

```html
<!-- Primary button -->
<p-button variant="primary">Save</p-button>

<!-- Destructive button -->
<p-button variant="destructive">Delete product</p-button>

<!-- Disabled state -->
<p-button disabled>Unavailable</p-button>

<!-- Loading state -->
<p-button loading>Saving…</p-button>

<!-- Link button -->
<p-button url="https://shopify.com" external>Visit Shopify</p-button>
```

---

### Forms

#### TextField

The `<p-text-field>` component lets merchants enter and edit text.

**Attributes**

| Attribute     | Type    | Default  | Description                                                |
|---------------|---------|----------|------------------------------------------------------------|
| `label`       | string  | —        | Visible label above the field. **Required.**               |
| `value`       | string  | `""`     | Current field value.                                       |
| `type`        | string  | `"text"` | HTML input type: `"text"`, `"number"`, `"email"`, `"password"`, `"search"`, `"tel"`, `"url"`. |
| `placeholder` | string  | —        | Placeholder text shown when the field is empty.            |
| `help-text`   | string  | —        | Descriptive text below the field.                          |
| `error`       | string  | —        | Error message. When set, the field renders in error state. |
| `disabled`    | boolean | `false`  | Prevents interaction.                                      |
| `read-only`   | boolean | `false`  | Value can be read but not changed.                         |
| `multiline`   | boolean | `false`  | Renders a `<textarea>` instead of `<input>`.               |
| `auto-complete`| string | —        | Maps to the `autocomplete` HTML attribute.                 |
| `max-length`  | number  | —        | Maximum allowed character count.                           |
| `prefix`      | string  | —        | Text displayed before the input value.                     |
| `suffix`      | string  | —        | Text displayed after the input value.                      |

**Events**

| Event      | Description                        |
|------------|------------------------------------|
| `p-change` | Fires when the value changes.      |
| `p-focus`  | Fires when the field gains focus.  |
| `p-blur`   | Fires when the field loses focus.  |

**Examples**

```html
<!-- Basic text field -->
<p-text-field label="Product title" placeholder="Short sleeve T-shirt"></p-text-field>

<!-- With help text -->
<p-text-field
  label="Email"
  type="email"
  help-text="We'll use this address for order confirmations."
></p-text-field>

<!-- With error -->
<p-text-field
  label="Price"
  type="number"
  error="Price must be greater than zero."
  value="-5"
></p-text-field>

<!-- Multiline -->
<p-text-field
  label="Description"
  multiline
  placeholder="Describe your product…"
></p-text-field>
```

---

#### Select

The `<p-select>` component lets merchants choose a single value from a list.

**Attributes**

| Attribute   | Type    | Default | Description                                   |
|-------------|---------|---------|-----------------------------------------------|
| `label`     | string  | —       | Visible label. **Required.**                  |
| `options`   | JSON    | `[]`    | Array of `{ label, value }` option objects.   |
| `value`     | string  | —       | Currently selected value.                     |
| `help-text` | string  | —       | Descriptive text below the select.            |
| `error`     | string  | —       | Error message.                                |
| `disabled`  | boolean | `false` | Prevents interaction.                         |

**Events**

| Event      | Description                                   |
|------------|-----------------------------------------------|
| `p-change` | Fires when the selected value changes.        |

**Examples**

```html
<p-select
  label="Country"
  options='[
    { "label": "Australia", "value": "AU" },
    { "label": "Canada",    "value": "CA" },
    { "label": "Ireland",   "value": "IE" },
    { "label": "United Kingdom", "value": "GB" },
    { "label": "United States",  "value": "US" }
  ]'
  value="GB"
></p-select>
```

---

#### Checkbox

The `<p-checkbox>` component lets merchants toggle a single setting on or off.

**Attributes**

| Attribute   | Type    | Default | Description                                   |
|-------------|---------|---------|-----------------------------------------------|
| `label`     | string  | —       | Visible label. **Required.**                  |
| `checked`   | boolean | `false` | Whether the checkbox is checked.              |
| `indeterminate` | boolean | `false` | Shows an indeterminate (mixed) state.     |
| `help-text` | string  | —       | Descriptive text below the checkbox.          |
| `error`     | string  | —       | Error message.                                |
| `disabled`  | boolean | `false` | Prevents interaction.                         |

**Events**

| Event      | Description                        |
|------------|------------------------------------|
| `p-change` | Fires when the checked state changes. |

**Examples**

```html
<!-- Unchecked -->
<p-checkbox label="Subscribe to newsletter"></p-checkbox>

<!-- Checked -->
<p-checkbox label="Agree to terms and conditions" checked></p-checkbox>

<!-- With help text -->
<p-checkbox
  label="Email me with news and offers"
  help-text="You can unsubscribe at any time."
></p-checkbox>
```

---

#### RadioButton

The `<p-radio-button>` component lets merchants choose a single option from a related set.

**Attributes**

| Attribute   | Type    | Default | Description                                    |
|-------------|---------|---------|------------------------------------------------|
| `label`     | string  | —       | Visible label. **Required.**                   |
| `name`      | string  | —       | Groups related radio buttons together.         |
| `value`     | string  | —       | Value submitted with the form.                 |
| `checked`   | boolean | `false` | Whether this option is selected.               |
| `help-text` | string  | —       | Descriptive text below the radio button.       |
| `disabled`  | boolean | `false` | Prevents interaction.                          |

**Events**

| Event      | Description                              |
|------------|------------------------------------------|
| `p-change` | Fires when this radio button is selected. |

**Examples**

```html
<p-radio-button label="Standard shipping — free"   name="shipping" value="standard" checked></p-radio-button>
<p-radio-button label="Express shipping — £9.99"   name="shipping" value="express"></p-radio-button>
<p-radio-button label="Next-day shipping — £19.99" name="shipping" value="nextday"></p-radio-button>
```

---

### Feedback Indicators

#### Badge

The `<p-badge>` component informs merchants about the status of an object or action.

**Attributes**

| Attribute  | Type   | Default     | Description                                                                       |
|------------|--------|-------------|-----------------------------------------------------------------------------------|
| `status`   | string | —           | Colour/meaning: `"success"`, `"info"`, `"attention"`, `"warning"`, `"critical"`. |
| `progress` | string | —           | Partially filled icon: `"incomplete"`, `"partiallyComplete"`, `"complete"`.       |
| `size`     | string | `"medium"`  | Size: `"small"`, `"medium"`.                                                      |

**Examples**

```html
<p-badge>Draft</p-badge>
<p-badge status="success">Active</p-badge>
<p-badge status="attention">On hold</p-badge>
<p-badge status="critical">Action required</p-badge>
<p-badge status="info" progress="partiallyComplete">In progress</p-badge>
```

---

#### Banner

The `<p-banner>` component informs merchants about important changes or persistent conditions.

**Attributes**

| Attribute          | Type    | Default | Description                                                                  |
|--------------------|---------|---------|------------------------------------------------------------------------------|
| `title`            | string  | —       | Banner heading.                                                              |
| `status`           | string  | —       | `"success"`, `"info"`, `"warning"`, `"critical"`.                            |
| `action-content`   | string  | —       | Label for the primary action button.                                         |
| `secondary-action-content` | string | — | Label for the secondary action link.                              |
| `dismissible`      | boolean | `false` | Shows a close button.                                                        |

**Events**

| Event       | Description                              |
|-------------|------------------------------------------|
| `p-action`  | Fires when the primary action is clicked. |
| `p-dismiss` | Fires when the dismiss button is clicked. |

**Examples**

```html
<!-- Informational -->
<p-banner title="Order archived" status="info">
  This order has been archived and is read-only.
</p-banner>

<!-- Success with action -->
<p-banner
  title="Your shipping label is ready"
  status="success"
  action-content="Print label"
  dismissible
>
  Download and print the label before dispatch.
</p-banner>

<!-- Critical -->
<p-banner title="Payment failed" status="critical">
  Your most recent payment was declined. Please update your billing details.
</p-banner>
```

---

#### Spinner

The `<p-spinner>` component provides feedback for a loading state.

**Attributes**

| Attribute            | Type   | Default    | Description                          |
|----------------------|--------|------------|--------------------------------------|
| `size`               | string | `"large"`  | Size: `"small"`, `"large"`.          |
| `accessibility-label`| string | `"Loading"`| Screen reader text. **Required.**    |

**Examples**

```html
<!-- Default spinner -->
<p-spinner accessibility-label="Loading products"></p-spinner>

<!-- Small spinner inline with content -->
<p-spinner size="small" accessibility-label="Saving"></p-spinner>
```

---

### Structure

#### Card

The `<p-card>` component groups related content and actions.

**Attributes**

| Attribute    | Type    | Default | Description                             |
|--------------|---------|---------|-----------------------------------------|
| `title`      | string  | —       | Card heading.                           |
| `sectioned`  | boolean | `false` | Automatically wraps children in sections.|
| `subdued`    | boolean | `false` | Applies a subdued background style.     |

**Slots**

| Slot      | Description                          |
|-----------|--------------------------------------|
| *(default)* | Card body content.                 |
| `actions` | Primary and secondary card actions.  |

**Examples**

```html
<p-card title="Online store dashboard" sectioned>
  <p>View a summary of your online store's performance.</p>
</p-card>

<p-card title="Products" subdued>
  <p slot="actions">
    <p-button url="/products/new" variant="plain">Add product</p-button>
  </p>
  <p>You have 42 products in your store.</p>
</p-card>
```

---

#### Page

The `<p-page>` component builds the outer wrapper of a page, including the page title and associated actions.

**Attributes**

| Attribute             | Type    | Default | Description                                           |
|-----------------------|---------|---------|-------------------------------------------------------|
| `title`               | string  | —       | Page heading.                                         |
| `subtitle`            | string  | —       | Optional subtitle beneath the heading.                |
| `back-action-content` | string  | —       | Label for the back-navigation link.                   |
| `back-action-url`     | string  | —       | URL for the back-navigation link.                     |
| `full-width`          | boolean | `false` | Expands the page to the full container width.         |
| `narrow-width`        | boolean | `false` | Constrains the page to a narrower reading width.      |

**Slots**

| Slot             | Description                   |
|------------------|-------------------------------|
| *(default)*      | Page content.                 |
| `primary-action` | Primary action button.        |
| `secondary-actions` | Secondary action buttons.  |
| `action-groups`  | Grouped overflow actions.     |

**Examples**

```html
<p-page
  title="Products"
  back-action-content="Home"
  back-action-url="/"
>
  <p-button slot="primary-action" variant="primary" url="/products/new">
    Add product
  </p-button>

  <!-- Page body goes here -->
  <p-card sectioned>
    <p>Your product list will appear here.</p>
  </p-card>
</p-page>
```

---

#### Layout

The `<p-layout>` component arranges content using a responsive grid.

**Variants** (applied via children):

| Element                   | Description                                      |
|---------------------------|--------------------------------------------------|
| `<p-layout-section>`      | A full-width section.                            |
| `<p-layout-section oneHalf>` | A section that takes half the available width. |
| `<p-layout-section oneThird>` | A section that takes a third of the width.  |
| `<p-layout-annotated-section>` | A two-column layout with a title/description on the left. |

**Examples**

```html
<!-- Two-column layout -->
<p-layout>
  <p-layout-section one-half>
    <p-card title="Sales" sectioned>
      <p>$4,200 this month</p>
    </p-card>
  </p-layout-section>

  <p-layout-section one-half>
    <p-card title="Orders" sectioned>
      <p>134 orders this month</p>
    </p-card>
  </p-layout-section>
</p-layout>

<!-- Annotated layout -->
<p-layout>
  <p-layout-annotated-section
    title="Store details"
    description="Shopify and your customers will use this information to contact you."
  >
    <p-card sectioned>
      <p-text-field label="Store name"></p-text-field>
      <p-text-field label="Account email" type="email"></p-text-field>
    </p-card>
  </p-layout-annotated-section>
</p-layout>
```

---

### Overlays

#### Modal

The `<p-modal>` component interrupts merchants with urgent information, details, or actions.

**Attributes**

| Attribute              | Type    | Default | Description                                            |
|------------------------|---------|---------|--------------------------------------------------------|
| `open`                 | boolean | `false` | Whether the modal is visible.                          |
| `title`                | string  | —       | Modal heading. **Required.**                           |
| `primary-action-content` | string | —     | Label for the primary button.                          |
| `secondary-action-content` | string | — | Label for the secondary button.                       |
| `destructive`          | boolean | `false` | Marks the primary action as destructive (red).         |
| `large`                | boolean | `false` | Increases modal width.                                 |

**Events**

| Event                    | Description                                      |
|--------------------------|--------------------------------------------------|
| `p-close`                | Fires when the modal is dismissed.               |
| `p-primary-action`       | Fires when the primary action button is clicked. |
| `p-secondary-action`     | Fires when the secondary action button is clicked.|

**Examples**

```html
<p-button id="open-modal" variant="primary">Delete product</p-button>

<p-modal
  id="confirm-modal"
  title="Delete product?"
  primary-action-content="Delete"
  secondary-action-content="Cancel"
  destructive
>
  Are you sure you want to delete <strong>Short sleeve T-shirt</strong>? 
  This action cannot be reversed.
</p-modal>

<script>
  const modal = document.getElementById('confirm-modal');
  document.getElementById('open-modal').addEventListener('click', () => {
    modal.open = true;
  });
  modal.addEventListener('p-close', () => { modal.open = false; });
  modal.addEventListener('p-secondary-action', () => { modal.open = false; });
  modal.addEventListener('p-primary-action', () => {
    // perform delete
    modal.open = false;
  });
</script>
```

---

#### Popover

The `<p-popover>` component displays a small overlay when its trigger is activated, used for contextual actions or information.

**Attributes**

| Attribute    | Type    | Default   | Description                                              |
|--------------|---------|-----------|----------------------------------------------------------|
| `active`     | boolean | `false`   | Whether the popover is visible.                          |
| `preferred-alignment` | string | `"left"` | Horizontal alignment: `"left"`, `"right"`, `"center"`. |
| `preferred-position`  | string | `"below"` | Vertical position: `"above"`, `"below"`, `"mostSpace"`. |
| `full-width` | boolean | `false`   | Stretches the popover to match the activator width.      |

**Slots**

| Slot        | Description                          |
|-------------|--------------------------------------|
| `activator` | The element that toggles the popover.|
| *(default)* | Popover content.                     |

**Examples**

```html
<p-popover id="actions-popover">
  <p-button slot="activator" disclosure>More actions</p-button>

  <p-action-list>
    <p-action-list-item>Duplicate</p-action-list-item>
    <p-action-list-item>Archive</p-action-list-item>
    <p-action-list-item destructive>Delete</p-action-list-item>
  </p-action-list>
</p-popover>

<script>
  const popover = document.getElementById('actions-popover');
  popover.querySelector('[slot="activator"]').addEventListener('click', () => {
    popover.active = !popover.active;
  });
</script>
```

---

#### Tooltip

The `<p-tooltip>` component displays additional information about an element when a merchant hovers over or focuses it.

**Attributes**

| Attribute    | Type   | Default   | Description                                            |
|--------------|--------|-----------|--------------------------------------------------------|
| `content`    | string | —         | Tooltip text. **Required.**                            |
| `preferred-position` | string | `"above"` | Position: `"above"`, `"below"`, `"mostSpace"`. |
| `active`     | boolean | `false`  | Forces the tooltip to always be visible (for debugging).|

**Slots**

| Slot        | Description                              |
|-------------|------------------------------------------|
| *(default)* | The element the tooltip is attached to.  |

**Examples**

```html
<!-- Icon with tooltip -->
<p-tooltip content="Edit product details">
  <p-button variant="plain" icon="EditMinor">Edit</p-button>
</p-tooltip>

<!-- Disabled button with tooltip -->
<p-tooltip content="Upgrade your plan to use this feature">
  <p-button disabled>Export CSV</p-button>
</p-tooltip>
```

---

### Images & Icons

#### Icon

The `<p-icon>` component renders an SVG icon from the Polaris icon set.

**Attributes**

| Attribute     | Type   | Default | Description                                               |
|---------------|--------|---------|-----------------------------------------------------------|
| `source`      | string | —       | Icon name from `@shopify/polaris-icons`. **Required.**    |
| `color`       | string | —       | Icon colour token: `"base"`, `"subdued"`, `"critical"`, `"interactive"`, `"warning"`, `"highlight"`, `"success"`, `"primary"`. |
| `backdrop`    | boolean| `false` | Adds a background colour behind the icon.                 |
| `accessibility-label` | string | — | Screen-reader text (use when icon conveys meaning alone). |

**Examples**

```html
<!-- Simple icon -->
<p-icon source="CircleTickMajor" color="success"></p-icon>

<!-- Icon with accessible label -->
<p-icon source="AlertMinor" color="critical" accessibility-label="Error"></p-icon>

<!-- Icon with backdrop -->
<p-icon source="ChecklistMajor" backdrop></p-icon>
```

---

## Theming & Customisation

All Polaris design tokens are exposed as CSS custom properties on the `:root` element. Override them to customise your theme:

```css
:root {
  /* Colours */
  --p-color-bg:              #f6f6f7;
  --p-color-bg-surface:      #ffffff;
  --p-color-bg-interactive:  #008060;
  --p-color-text:            #202223;
  --p-color-text-interactive:#1a0dab;
  --p-color-border:          #c9cccf;

  /* Border radius */
  --p-border-radius-base:    0.4rem;
  --p-border-radius-large:   0.8rem;

  /* Shadows */
  --p-shadow-card:           0 0 0 1px rgba(63,63,68,.05), 0 1px 3px 0 rgba(63,63,68,.15);

  /* Typography */
  --p-font-size-75:          1.2rem;
  --p-font-size-100:         1.4rem;
  --p-font-size-200:         1.6rem;
  --p-font-size-300:         2.0rem;
  --p-font-size-400:         2.4rem;
}
```

---

## Accessibility

Every Polaris web component is built to meet **WCAG 2.1 Level AA** requirements:

- Semantic HTML elements are used wherever possible.
- All interactive components are keyboard-navigable.
- ARIA attributes (`aria-label`, `aria-live`, `aria-expanded`, etc.) are managed automatically.
- Focus management is handled for modal dialogs and popovers.
- Colour contrast ratios meet or exceed 4.5:1 for normal text and 3:1 for large text.

When adding custom content inside a component, ensure:
1. Adequate colour contrast between text and background.
2. Images and icons have descriptive `alt` text or `accessibility-label` attributes.
3. Form fields always have an associated visible label.

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository and create a feature branch (`git checkout -b feature/my-change`).
2. Make your changes and add tests where appropriate.
3. Run `npm test` to ensure all tests pass.
4. Submit a pull request with a clear description of your change.

Please read our [Code of Conduct](./CODE_OF_CONDUCT.md) before contributing.

---

## Licence

This project is licensed under the [MIT Licence](./LICENSE).
