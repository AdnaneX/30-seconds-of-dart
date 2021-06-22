---
title: get
---

Try to convert function get from javascript to dart.
##### Javasctipt
```js
const get = (from, ...selectors) =>
  [...selectors].map(s =>
    s
      .replace(/\[([^\[\]]*)\]/g, '.$1.')
      .split('.')
      .filter(t => t !== '')
      .reduce((prev, cur) => prev && prev[cur], from)
  );
```

```js
const obj = {
  selector: { to: { val: 'val to select' } },
  target: [1, 2, { a: 'test' }],
};
get(obj, 'selector.to.val', 'target[0]', 'target[2].a');
// ['val to select', 1, 'test']
```

##### Dart

```dart
print( 'a[0].b[0].c'.replaceAllMapped(RegExp(r"\[([^\[\]]*)\]"), (Match match) => ".${match[1]}.").split('.').where((item) => item != null && item != ''));
```
