---
outline: 'deep'
---
# style 
- `type`: `Object`  

条形图样式配置


### style.barWidth

- `type`: `number`

条形图的宽度配置

```javascript
style: {
    barWidth: 16, // 条形图的宽度
}
```


### style.shape

- `type`: `string`


条形图顶部配置,`topTriangle`条形图顶部为三角形,同时也可以引入图片进行配置

```javascript
style: {
    shape: 'topTriangle', // 条形图顶部三角形
}
```

也可以配置图片:


```javascript
import arrowMainBD from '@/assets/img/arrow_main_bluedark.png'
style: {
    shape: arrowMainBD, // 
}
```

