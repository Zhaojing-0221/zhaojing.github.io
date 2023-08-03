---
outline: "deep"
---

# line

- `type`: `Object`

线条相关的内容：线条是否平滑、线条上的点(主要在折线图上使用)

#### line.smooth

- `type`: `Boolean`

线条是否平滑，默认不平滑，可通过传入`true`设置线段为平滑曲线。

```javascript
line: {
    smooth: true, // 平滑
}
```

线条为平滑时效果如下图：

![An image](../public/line-smooth.png)

#### line.point
- `type`: `Boolean`

线条上是否显示对应的点，默认不显示，可通过传入`true`设置线段的点。

```javascript
line: {
    point: true, // 显示对应的点
}
```