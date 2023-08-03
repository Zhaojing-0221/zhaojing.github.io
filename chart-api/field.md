---
outline: 'deep'
---

#  xField

- `type`: `String`
- `default`: `'x'`

`x`轴字段。

以哪个字段作为`x`轴的数据(默认以`data`数据中的`x`字段)：

```javascript
xField = "genre"; // 以"genre"字段的值作为x轴的数据
```

# yField

- `type`: `String`
- `default`: `'y'`

`y`轴字段。

以哪个字段作为`y`轴的数据(默认以`data`数据中的`y`字段)：

```javascript
yField = "sold"; //以"sold"字段的值作为y轴的数据
```

# seriesField

- `type`: `String`
- `default`: `'undefined'`
- `required`: `False`

多组图形的分组字段。

当有多组图形：多条面积图或多条折线图，通过这个数据字段对数据进行分组：

```javascript
const data = [
    { genre: 'Sports', sold: 275, age: 10, team: 'team1' },
    { genre: 'Strategy', sold: 115, age: 20, team: 'team1' },
    { genre: 'Sports', sold: 120, age: 20, team: 'team2' },
    { genre: 'Strategy', sold: 350, age: 10, team: 'team2' },
    { genre: 'Sports', sold: 150, , age: 10, team: 'team3' },
    { genre: 'Strategy', sold: 150, , age: 10, team: 'team3' },
];
seriesField = 'team'
```

以上的`data`和`seriesField`配置最终会将数据分为三组，展示三条线段：

```javascript
const data1 = [
    { genre: 'Sports', sold: 275, age: 10, team: 'team1' },
    { genre: 'Strategy', sold: 115, age: 20, team: 'team1' },
];

const data2 = [
    { genre: 'Sports', sold: 120, age: 20, team: 'team2' },
    { genre: 'Strategy', sold: 350, age: 10, team: 'team2' },
]

const data3 = {
    { genre: 'Sports', sold: 150, , age: 10, team: 'team3' },
    { genre: 'Strategy', sold: 150, , age: 10, team: 'team3' },
}
```