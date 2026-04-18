# Icon

Icons are used to visually communicate core parts of the product and available actions. They can act as wayfinding tools to help merchants more easily understand where they are in the product, and common interactions that are available to them.

## Best practices

Icons should:

- Use established icons from the Polaris icon set wherever possible.
- Be accompanied by a visible text label wherever the icon's meaning may be ambiguous.
- Use an `accessibility-label` when used without a visible text label.
- Not be used purely for decoration with no semantic meaning.

## Content guidelines

`accessibility-label` should:

- Describe the meaning or action, not the icon's appearance.
- Be concise: "Delete", "Search", "Toggle navigation".

## Examples

### Basic icon

```html
<p-icon source="CircleTickMajor"></p-icon>
```

### Icon with colour

Use the `color` attribute to apply a semantic colour.

```html
<p-icon source="CircleTickMajor"  color="success"></p-icon>
<p-icon source="AlertMinor"       color="warning"></p-icon>
<p-icon source="CircleAlertMajor" color="critical"></p-icon>
<p-icon source="InfoMinor"        color="highlight"></p-icon>
```

### Icon with accessible label

Use when the icon is the only means of communicating an action or meaning.

```html
<p-button variant="plain" icon="DeleteMinor">
  <p-icon source="DeleteMinor" accessibility-label="Delete product"></p-icon>
</p-button>
```

### Icon with backdrop

Use a backdrop to make an icon stand out from its surroundings.

```html
<p-icon source="ProductsMajor" backdrop></p-icon>
```

## Props

| Prop                  | Type    | Default | Description |
|-----------------------|---------|---------|-------------|
| `source`              | string  | —       | Icon identifier from `@shopify/polaris-icons`. **Required.** |
| `color`               | string  | `"base"` | Icon colour. Options: `"base"`, `"subdued"`, `"critical"`, `"interactive"`, `"warning"`, `"highlight"`, `"success"`, `"primary"`. |
| `backdrop`            | boolean | `false` | Adds a rounded background behind the icon. |
| `accessibility-label` | string  | —       | Screen-reader description. Use when the icon conveys meaning without accompanying text. |

## Available icons

The full Polaris icon set is available in the `@shopify/polaris-icons` package. Common icons include:

| Icon name              | Usage |
|------------------------|-------|
| `AddMinor`             | Add or create a new item. |
| `AlertMinor`           | Warning or attention required. |
| `ArchiveMinor`         | Archive content. |
| `ArrowLeftMinor`       | Navigate back. |
| `ArrowRightMinor`      | Navigate forward. |
| `AttachmentMajor`      | File attachments. |
| `CancelMinor`          | Close or cancel. |
| `CartMajor`            | Shopping cart. |
| `ChecklistMajor`       | Task lists. |
| `CircleTickMajor`      | Success or confirmation. |
| `CircleAlertMajor`     | Error state. |
| `CustomersMajor`       | Customer management. |
| `DeleteMinor`          | Delete or remove. |
| `EditMinor`            | Edit or modify. |
| `ExportMinor`          | Export data. |
| `FilterMajor`          | Filter content. |
| `HomeMajor`            | Home / dashboard. |
| `ImportMinor`          | Import data. |
| `InfoMinor`            | Informational content. |
| `MobileHamburgerMajor` | Mobile navigation menu. |
| `OrdersMajor`          | Orders management. |
| `PrintMinor`           | Print. |
| `ProductsMajor`        | Products management. |
| `SearchMinor`          | Search. |
| `SettingsMajor`        | Settings. |
| `SortMinor`            | Sort content. |
| `ViewMinor`            | View or preview. |

For the complete list, see the [Polaris Icons catalogue](https://polaris.shopify.com/icons).

## Accessibility

- An icon without text must have an `accessibility-label`; without it, screen readers will skip the element entirely.
- An icon used alongside visible text does not need an `accessibility-label` — use `aria-hidden="true"` to hide it from the accessibility tree.

```html
<!-- Icon alongside text — hide from screen readers -->
<p-button>
  <p-icon source="AddMinor" aria-hidden="true"></p-icon>
  Add product
</p-button>

<!-- Icon without text — provide accessible label -->
<p-button variant="plain">
  <p-icon source="DeleteMinor" accessibility-label="Delete product"></p-icon>
</p-button>
```
