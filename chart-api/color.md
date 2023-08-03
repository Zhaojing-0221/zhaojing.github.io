---
outline: 'deep'
---

# color

- `type`: `string | Array`

图表的颜色，可传递字符串或者数组。如果图表项是多组颜色建议使用数组形式，单个颜色使用字符串即可。

```javascript
// 图表项的多组颜色
color = ["#934EEC", "#1E91F5", "#8DB3DF"];

// 图表项的单个颜色
color = "#FFF";
```

### fillColor

- `type`: `string | Array`

填充颜色，主要为面积图使用。 多组颜色建议使用数组形式，单个颜色使用字符串即可。

```javascript
// 面积填充色：多组颜色
const fillColor = [
  "l(270) 0:#26324B30 0.3:#26314A 1:#934EEC",
  "l(270) 0:#26324B 0.3:#26314A 1:#1E91F5",
  "l(270) 0:#26324B 0.2:#26314A 1:#8DB3DF",
];
// 面积填充色：单个颜色
const fillColor = "#FFF";
```

