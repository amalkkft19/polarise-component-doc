# Modal

Modals are overlays that require merchants to take an action before they can continue interacting with the rest of Shopify. They can be disruptive and should be used sparingly.

## Best practices

Modals should:

- Require merchants to take an action they need to take immediately.
- Present a critical action that can't wait, or a decision that needs to be made now.
- Communicate important information.
- Provide instructions merchants need before continuing.

Modals should NOT be used to:

- Display large amounts of content.
- Confirm non-destructive actions — use inline confirmation instead.
- Be triggered automatically or by hover.

## Content guidelines

### Title

- Use a noun or noun phrase that describes the action: "Delete product?", "Unsaved changes".
- Avoid yes/no questions.

### Body text

- Describe what will happen if the merchant confirms.
- Be concise — a sentence or two at most.

### Primary action

- Use a verb that confirms the action: "Delete", "Save", "Send".
- For destructive actions, the button is styled red.

### Secondary action

- Usually "Cancel" — gives merchants a way out.

## Examples

### Basic modal

```html
<p-modal
  id="my-modal"
  title="Import products"
  primary-action-content="Import"
  secondary-action-content="Cancel"
>
  <p>
    Your CSV file has been uploaded and will be imported as products
    to your store. This can take up to 5 minutes.
  </p>
</p-modal>

<script>
  const modal = document.getElementById('my-modal');
  document.getElementById('trigger-btn').addEventListener('click', () => {
    modal.open = true;
  });
  modal.addEventListener('p-close',            () => { modal.open = false; });
  modal.addEventListener('p-secondary-action', () => { modal.open = false; });
  modal.addEventListener('p-primary-action',   () => {
    // handle import
    modal.open = false;
  });
</script>
```

### Destructive modal

Use for actions that cannot be undone or are difficult to reverse.

```html
<p-modal
  title="Delete product?"
  primary-action-content="Delete"
  secondary-action-content="Cancel"
  destructive
>
  Are you sure you want to delete <strong>Short sleeve T-shirt</strong>?
  This action cannot be reversed.
</p-modal>
```

### Large modal

Use when you need more space for content such as a form.

```html
<p-modal
  title="Edit shipping address"
  primary-action-content="Save"
  secondary-action-content="Cancel"
  large
>
  <p-form-layout>
    <p-text-field label="First name"></p-text-field>
    <p-text-field label="Last name"></p-text-field>
    <p-text-field label="Address line 1"></p-text-field>
    <p-text-field label="City"></p-text-field>
    <p-select label="Country" options="[...]"></p-select>
  </p-form-layout>
</p-modal>
```

### Warning modal

Use to inform merchants about something important before proceeding.

```html
<p-modal
  title="Unsaved changes"
  primary-action-content="Discard changes"
  secondary-action-content="Continue editing"
  destructive
>
  If you leave this page, all unsaved changes will be lost.
</p-modal>
```

## Props

| Prop                       | Type    | Default | Description |
|----------------------------|---------|---------|-------------|
| `open`                     | boolean | `false` | Whether the modal is visible. |
| `title`                    | string  | —       | Modal heading. **Required.** |
| `primary-action-content`   | string  | —       | Label for the primary button. |
| `secondary-action-content` | string  | —       | Label for the secondary button. |
| `destructive`              | boolean | `false` | Styles the primary action as destructive (red). |
| `large`                    | boolean | `false` | Increases the width of the modal. |
| `instant`                  | boolean | `false` | Skips the opening/closing animation. |
| `loading`                  | boolean | `false` | Shows a loading spinner in the footer. |

## Events

| Event                  | Description |
|------------------------|-------------|
| `p-close`              | Fires when the modal is dismissed (close button or Escape key). |
| `p-primary-action`     | Fires when the primary action button is clicked. |
| `p-secondary-action`   | Fires when the secondary action button is clicked. |

## Slots

| Slot        | Description |
|-------------|-------------|
| *(default)* | Modal body content. |
| `footer`    | Custom footer content (replaces the default action buttons). |

## Accessibility

- The modal container uses `role="dialog"` and `aria-modal="true"`.
- `aria-labelledby` links the dialog to its title.
- Focus is automatically moved to the modal when it opens and returned to the trigger element when it closes.
- The Escape key always closes the modal.
- The background page is not focusable or scrollable while the modal is open.
