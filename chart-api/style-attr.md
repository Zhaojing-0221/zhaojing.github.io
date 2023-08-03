---
outline: 'deep'
---

# 通用属性

| 属性名  |	描述 |
| :---   | :--- |
|fillOpacity	|用于设置图形填充颜色的透明度，默认值是 1。
|stroke	        |描边色、渐变或纹理，默认值为空；
|strokeOpacity	|用于设置边颜色的透明度，默认值是 1。
|shadowColor	|描述阴影颜色的属性
|shadowBlur	    |描述模糊效果程度的属性； 它既不对应像素值也不受当前转换矩阵的影响。 默认值是 0
|shadowOffsetX	|描述阴影水平偏移距离的属性。
|shadowOffsetY	|描述阴影垂直偏移距离的属性。
|opacity 	    |设置图形和图片透明度的属性，默认值是 1。 数值的范围从 0.0 （完全透明）到 1.0 （完全不透明）


# 线条属性

| 属性名  |	描述 |
| :---   | :--- |
|lineWidth|线段的宽度，当获取属性值时，它可以返回当前的值（默认值是 1.0 ）。 当给属性赋值时， 0、 负数、 Infinity 和 NaN 都会被忽略；除此之外，都会被赋予一个新值
|lineDash|	设置线的虚线样式，可以指定一个数组。一组描述交替绘制线段和间距（坐标空间单位）长度的数字。 如果数组元素的数量是奇数， 数组的元素会被复制并重复。例如， [5, 15, 25] 会变成 [5, 15, 25, 5, 15, 25]。这个属性取决于浏览器是否支持 setLineDash() 函数，详情参考 setLineDash。


# 文本属性

| 属性名  |	描述 |
| :---   | :--- |
|textAlign|	设置文本内容的当前对齐方式, 支持的属性：'start', 'center', 'end', 'left', 'right'
|textBaseline|	设置在绘制文本时使用的当前文本基线, 支持的属性：'top', 'hanging', 'middle', 'alphabetic', 'ideographic', 'bottom'
|fontStyle|	规定字体样式。可能的值：'normal', 'italic', 'oblique'
|fontSize|	规定字号，以像素计
|fontFamily|	规定字体系列
|fontWeight|	规定字体的粗细。可能的值：'normal', 'bold', 'bolder', 'lighter', '100', '200, '300', '400','500', '600', '700', '800', '900'
|fontVariant|	规定字体变体。可能的值：'normal', 'small-caps'
|lineHeight|	规定行高，以像素计