---
outline: 'deep'
---
# scrollbar 
- `type`: `Object`  

滚动条组件，Scrollbar，可以让用户在数据量较大的情况下一次只关注局部的数据。
滚动条默认是关闭的，传入配置开启滚动条.


### scrollbar.max

- `type`: `number`

当data的长度超过`max`指定的条数后,会开启滚动条效果。

```javascript
scrollbar: {
    max: 20, // 当data超过20条的时候滚动条开启
}
```

::: tip
在`blueDark`和`lightOrange`主题中，`max`的默认值为`31`条，即当图表的`data`长度大于`31`时，就会开启`scrollbar`，无需任何配置。
:::




### scrollbar.categorySize

- `type`: `number`


每一组数据在图表上的间距

```javascript
scrollbar: {
    categorySize: 100, // 坐标轴每一组数据的宽度
}
```
