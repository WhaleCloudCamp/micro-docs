# Location

## 获取当前位置

```js
const location = await alita.location.getLocation();
```

### 参数

无

### 响应

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| latitude | number | 纬度，范围为 -90~90，负数表示南纬 |
| longitude | number | 经度，范围为 -180~180，负数表示西经 |