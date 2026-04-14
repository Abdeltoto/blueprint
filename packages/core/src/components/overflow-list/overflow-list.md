@# Overflow list

**OverflowList** takes a generic list of items and renders as many items as can fit inside its container. Overflowed
items that do not fit are collapsed into a single element. The visible items will be recomputed when a resize is
detected.

The `items` prop accepts an array of generic objects. The required `visibleItemRenderer` callback prop determines the
appearance of a visible item. The required `overflowRenderer` callback prop receives all overflowed items and renders
the overflow indicator.

This component uses [the `ResizeObserver` API][resizeobserver] to efficiently detect when its dimensions change. Use
the `observeParents` prop to watch for resizing further up in the DOM tree.

[resizeobserver]: https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver

@## Import

```ts copy
import { OverflowList } from "@blueprintjs/core";
```

@reactExample OverflowListExample

@## Usage notes

The `visibleItemRenderer` callback is invoked inside an internal `.map()`, so you **must** return an element with a
unique `key` prop. Otherwise React will emit a warning: _Each child in a list should have a unique "key" prop_.

```tsx
// ✅ Correct — element includes a unique `key`
visibleItemRenderer={(item) => <Tag key={item.id}>{item.name}</Tag>}

// ❌ Incorrect — will cause a React key warning
visibleItemRenderer={(item) => <Tag>{item.name}</Tag>}
```

@## Props interface

@interface OverflowListProps
