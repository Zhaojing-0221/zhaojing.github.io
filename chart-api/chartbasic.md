---
outline: 'deep'
---

# chartBasic
- `required`: `可选`

图表对象的一些基础配置，比如图表宽（`width`）高（`height`）、内边距(`padding`)以及图表的渲染引擎(`renderer`)等。如果没有`width`和`height`参数，图表容器的宽高会自适应父组件`DOM`元素的宽高，且渲染方式为`canvas`。

##### chartBasic.width

- `type`: `Number `

图表的宽度。

##### chartBasic.heigth

- `type`: `Number `

图表的高度。

:::tip

`width`和`height`都为可选参数，图表的宽高默认自适应父元素的宽高。

:::

##### chartBasic.padding

- `type`: `'auto' | Number | Number[]`
- `default`: `'auto'`

图表的内边距。

```javascript
chartBasic =  {
    width: 600,
    height: 280,
    padding: [10, 20, 30, 60]
}

````