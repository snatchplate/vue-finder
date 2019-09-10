# Customization

Vue Finder provides some options to customize its look.

## Theming

The `Finder` component accepts a `theme` prop that allows to customize some CSS properties:

```html
<Finder :tree="tree" :theme="theme" />
```

```js
// ...
data() {
  return {
    theme: {
      primaryColor: "#2196f3",
      arrowColor: "black",
      separatorColor: "#ccc",
      separatorWidth: "1px",
      dropZoneBgColor: "rgba(33, 150, 243, 0.2)",
      draggedItemBgColor: "rgba(33, 150, 243, 0.5)"
    }
  }
}
```

Here are the available properties:

| Name                 | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| `primaryColor`       | Primary color used for expanded items, dropzone borders...   |
| `arrowColor`         | Color of arrows in expandable items                          |
| `separatorColor`     | Border color of separators between lists                     |
| `separatorWidth`     | Width value of separators between lists                      |
| `dropZoneBgColor`    | Background color of drop zones (visible when Drag & Drop)    |
| `draggedItemBgColor` | Background color of dragged items (visible when Drag & Drop) |

## Item component

You can define a component to render items with the `itemComponent` prop. This component requires a `item` prop, that will
receive the data of the rendered item.

```html
<Finder :tree="tree" :itemComponent="itemComponent" />
```

```js
// ...
data() {
  return {
    itemComponent: {
      props: ["item"],
      template:
        "<div style="color: blue"><em>Name:</em> <strong>{{ item.label }}</strong></div>"
    }
  }
}
```

<FinderExample :useCustomItemComponent="true"/>

::: warning

The example above uses the `template` option to define the rendering of the component, so
the [runtime compiler](https://vuejs.org/v2/guide/installation.html#Runtime-Compiler-vs-Runtime-only) is needed.

You can also use a `render` function (in this case the runtime-only build is enough):

```js
itemComponent: {
  props: ["item"],
  render(h) {
    return h("div", this.item)
  }
}
```

:::