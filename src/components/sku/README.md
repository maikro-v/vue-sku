# Sku选择器

基于vue的sku选择器

### Attributes

| 参数 | 说明 | 类型 | 可选值 | 默认值 |
|---|---|---|---|---|
| skuData | 所有可选的sku数据，如果库存为0的数据不能选择就把库存为0的数据过滤掉 | array | - | - |
| specData | 规格列表 | array | - | - |

#### skuData sku数据格式
```javascript
  [
    {
      ..., // 其它属性
      spec: [ // 规格必须要存在此字段
        {
          key_id: 'key123', // 规格id，必须是唯一值
          value_id: 'v123', // 属性id，必须是唯一值
          value: '红色', // 属性名 
        },
        ...
      ]
    }
  ]
```

#### specData 规格数据格式
```javascript
  [
    {
      id: '1', // 规格id，必须是唯一值
      value: '颜色', // 规格名,
      spec: [
        {
          id: '2', // 属性id,必须是唯一值
          value: '红色', // 属性名称
        },
        ...
      ]
    },
    ...
  ]
```

### Methods

| 方法名 | 说明 | 参数 |
|---|---|---|
| on-change | 选择规格时调用 | currentSpec 当前所选的规格 |
| on-select | 选完规格时调用 | sku 规格所对应的sku数据 |
