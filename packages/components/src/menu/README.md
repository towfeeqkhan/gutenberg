# `Menu`

<div class="callout callout-alert">
This feature is still experimental. “Experimental” means this is an early implementation subject to drastic and breaking changes.
</div>

`Menu` displays a menu to the user (such as a set of actions or functions). The menu is rendered in a popover (this pattern is also known as a "Dropdown menu"), which is triggered by a button.

## Design guidelines

### Usage

#### When to use a `Menu`

Use a `Menu` when you want users to:

-   Choose an action or change a setting from a list, AND
-   Only see the available choices contextually.

`Menu` is a React component to render an expandable menu of buttons. It is similar in purpose to a `<select>` element, with the distinction that it does not maintain a value. Instead, each option behaves as an action button.

If you need to display all the available options at all times, consider using a Toolbar instead. Use a `Menu` to display a list of actions after the user interacts with a button.

**Do**
Use a `Menu` to display a list of actions after the user interacts with an icon.

**Don’t** use a `Menu` for important actions that should always be visible. Use a `Toolbar` instead.

**Don’t**
Don’t use a `Menu` for frequently used actions. Use a `Toolbar` instead.

#### Behavior

Generally, the parent button should indicate that interacting with it will show a `Menu`.

The parent button should retain the same visual styling regardless of whether the `Menu` is displayed or not.

#### Placement

The `Menu` should typically appear directly below, or below and to the left of, the parent button. If there isn’t enough space below to display the full `Menu`, it can be displayed instead above the parent button.

## Development guidelines

This component is still highly experimental, and it's not normally accessible to consumers of the `@wordpress/components` package.

The component exposes a set of components that are meant to be used in combination with each other in order to implement a `Menu` correctly.

### `Menu`

The root component, used to specify the menu's trigger and its contents.

#### Props

The component accepts the following props:

##### `trigger`: `React.ReactNode`

The button triggering the menu popover.

-   Required: yes

##### `children`: `React.ReactNode`

The contents of the menu (ie. one or more menu items).

-   Required: yes

##### `defaultOpen`: `boolean`

The open state of the menu popover when it is initially rendered. Use when not wanting to control its open state.

-   Required: no
-   Default: `false`

##### `open`: `boolean`

The controlled open state of the menu popover. Must be used in conjunction with `onOpenChange`.

-   Required: no

##### `onOpenChange`: `(open: boolean) => void`

Event handler called when the open state of the menu popover changes.

-   Required: no

##### `modal`: `boolean`

The modality of the menu popover. When set to true, interaction with outside elements will be disabled and only menu content will be visible to screen readers.

-   Required: no
-   Default: `true`

##### `placement`: ``'top' | 'top-start' | 'top-end' | 'right' | 'right-start' | 'right-end' | 'bottom' | 'bottom-start' | 'bottom-end' | 'left' | 'left-start' | 'left-end'`

The placement of the menu popover.

-   Required: no
-   Default: `'bottom-start'` for root-level menus, `'right-start'` for nested menus

##### `gutter`: `number`

The distance in pixels from the trigger.

-   Required: no
-   Default: `8` for root-level menus, `16` for nested menus

##### `shift`: `number`

The skidding of the popover along the anchor element. Can be set to negative values to make the popover shift to the opposite side.

-   Required: no
-   Default: `0` for root-level menus, `-8` for nested menus

### `Menu.Item`

Used to render a menu item.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The contents of the item

-   Required: yes

##### `prefix`: `React.ReactNode`

The contents of the item's prefix.

-   Required: no

##### `suffix`: `React.ReactNode`

The contents of the item's suffix.

-   Required: no

##### `hideOnClick`: `boolean`

Whether to hide the menu popover when the menu item is clicked.

-   Required: no
-   Default: `true`

##### `disabled`: `boolean`

Determines if the element is disabled.

-   Required: no
-   Default: `false`

### `Menu.CheckboxItem`

Used to render a checkbox item.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The contents of the item

-   Required: yes

##### `suffix`: `React.ReactNode`

The contents of the item's suffix.

-   Required: no

##### `hideOnClick`: `boolean`

Whether to hide the menu popover when the menu item is clicked.

-   Required: no
-   Default: `false`

##### `disabled`: `boolean`

Determines if the element is disabled.

-   Required: no
-   Default: `false`

##### `name`: `string`

The checkbox item's name.

-   Required: yes

##### `value`: `string`

The checkbox item's value, useful when using multiple checkbox items
associated to the same `name`.

-   Required: no

##### `checked`: `boolean`

The checkbox item's value, useful when using multiple checkbox items
associated to the same `name`.

-   Required: no

##### `defaultChecked`: `boolean`

The checked state of the checkbox menu item when it is initially rendered. Use when not wanting to control its checked state.

-   Required: no

##### `onChange`: `( event: React.ChangeEvent< HTMLInputElement > ) => void;`

Event handler called when the checked state of the checkbox menu item changes.

-   Required: no

### `Menu.RadioItem`

Used to render a radio item.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The contents of the item

-   Required: yes

##### `suffix`: `React.ReactNode`

The contents of the item's suffix.

-   Required: no

##### `hideOnClick`: `boolean`

Whether to hide the menu popover when the menu item is clicked.

-   Required: no
-   Default: `false`

##### `disabled`: `boolean`

Determines if the element is disabled.

-   Required: no
-   Default: `false`

##### `name`: `string`

The radio item's name.

-   Required: yes

##### `value`: `string | number`

The radio item's value.

-   Required: yes

##### `checked`: `boolean`

The checkbox item's value, useful when using multiple checkbox items
associated to the same `name`.

-   Required: no

##### `defaultChecked`: `boolean`

The checked state of the radio menu item when it is initially rendered. Use when not wanting to control its checked state.

-   Required: no

##### `onChange`: `( event: React.ChangeEvent< HTMLInputElement > ) => void;`

Event handler called when the checked radio menu item changes.

-   Required: no

### `Menu.ItemLabel`

Used to render the menu item's label.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The label contents.

-   Required: yes

### `Menu.ItemHelpText`

Used to render the menu item's help text.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The help text contents.

-   Required: yes

### `Menu.Group`

Used to group menu items.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The contents of the menu group (ie. an optional menu group label and one or more menu items).

-   Required: yes

### `Menu.GroupLabel`

Used to render a group label. The label text should be kept as short as possible.

#### Props

The component accepts the following props:

##### `children`: `React.ReactNode`

The contents of the menu group label.

-   Required: yes

### `Menu.Separator`

Used to render a visual separator.
