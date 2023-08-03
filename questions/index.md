---
outline: 'deep'
---
# 常见问题

### Q1：坐标轴被遮挡

当图表的`x`轴设置了对应的度量：

```javascript
axis: {
    xAxis: {
        scale: {
            ticks: ['00:00', '06:00', '12:00', '18:00', '24:00']
        }
    }
}
```
如果此时`x`轴的数据项不能完全匹配`ticks`中配置的数据，`x`轴就会出现显示不全的问题。

![An image](/questions/xaxis-scale-mismatch.png)


### Q2：面积图颜色切换
当修改数据时面积图颜色异常显示问题.
在面积图color参数，指明不同数据和颜色之间的对应关系即可（fillColor自动识别，无需传参） 

- 风格切换以后，对应的颜色也会同步切换，业务组件无需处理  
- color参数示例：
```javascript
color = { 
    总产量: 1, 
    综采一队: 2, 
    综采二队: 3, 
    综采三队: 4
}  
```
- 其中`key`对应的`value`为产品原型提供的色值的顺序。

<preview path="../examples/default/AreaLineColor.vue" title="基础样式" description=""></preview>

### Q3：面积图颜色高亮显示

* 降低将两侧面积区域的颜色

<preview path="../examples/default/AreaAnnotation.vue" title="基础样式" description=""></preview>
