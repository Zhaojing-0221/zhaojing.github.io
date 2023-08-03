---
outline: 'deep'
---
# transpose 
- `type`: `String`  

该参数主要为条形图的坐标系转化而使用。

默认`条形图`是纵向的条形图，可以通过设置`transpose: horizontal `该参数将条形图转化为横向的条形图。

### default

默认为纵向的条形图。

![纵向的条形图](/api/default-interval.png)

### horizontal

横向的条形图。

```javascript
transpose: horizontal
```

![横向的条形图](/api/horizontal-interval.png)

### mirror

当我们有两组数据时，默认条形图是以堆叠的方式展示的。

![默认堆叠的条形图](/api/two-series-data.png)


设置`transpose: mirror`可以让条形图转为镜像条形图。

```javascript
transpose: mirror
```

![横向的条形图](/api/default-mirror.png)

### horizontalMirror

当我们有两组数据时，设置`transpose: mirror`可以让条形图横向的镜像条形图。

```javascript
transpose: horizontalMirror

```

![横向的条形图](/api/transpose/horizontal-mirror.png)