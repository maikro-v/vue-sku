<template>
  <div class="home">
    <sku :sku-data="skuList" :spec-data="specList" @on-change="onSkuChange" @on-select="onSkuSelect" />
  </div>
</template>

<script>
import sku from '@/components/sku'
  export default {
    name: 'Home',
    components: { sku },
    data() {
      return {
        skuData: [
          {
            'id': 390,
            'uniqid': 'fCyn1mKj4zzL',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '89392246,39096481,85468638',
            'value': '红色,s,秋季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['89392246', '39096481', '85468638'],
              'value': ['红色', 's', '秋季']
            }
          },
          {
            'id': 391,
            'uniqid': '5ammbe5uf8eG',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '89392246,39096481,80386662',
            'value': '红色,s,夏季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['89392246', '39096481', '80386662'],
              'value': ['红色', 's', '夏季']
            }
          },
          {
            'id': 392,
            'uniqid': 'Kf01eC8K5eKH',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '89392246,39096481,29551310',
            'value': '红色,s,四季可穿',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['89392246', '39096481', '29551310'],
              'value': ['红色', 's', '四季可穿']
            }
          },
          {
            'id': 393,
            'uniqid': 'yb4b80rDOXKr',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '89392246,34394082,85468638',
            'value': '红色,m,秋季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 0,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['89392246', '34394082', '85468638'],
              'value': ['红色', 'm', '秋季']
            }
          },
          {
            'id': 394,
            'uniqid': 'yrLuz5mXWzvz',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '89392246,34394082,80386662',
            'value': '红色,m,夏季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['89392246', '34394082', '80386662'],
              'value': ['红色', 'm', '夏季']
            }
          },
          {
            'id': 395,
            'uniqid': '94u1uv5SHuP1',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '89392246,34394082,29551310',
            'value': '红色,m,四季可穿',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['89392246', '34394082', '29551310'],
              'value': ['红色', 'm', '四季可穿']
            }
          },
          {
            'id': 396,
            'uniqid': 'yTvP1G1uvrfu',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '96975150,39096481,85468638',
            'value': '黑色,s,秋季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 0,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['96975150', '39096481', '85468638'],
              'value': ['黑色', 's', '秋季']
            }
          },
          {
            'id': 397,
            'uniqid': '9ai5eyG1SC0O',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '96975150,39096481,80386662',
            'value': '黑色,s,夏季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 0,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['96975150', '39096481', '80386662'],
              'value': ['黑色', 's', '夏季']
            }
          },
          {
            'id': 398,
            'uniqid': 'L5KSPHqfWHTr',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '96975150,39096481,29551310',
            'value': '黑色,s,四季可穿',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['96975150', '39096481', '29551310'],
              'value': ['黑色', 's', '四季可穿']
            }
          },
          {
            'id': 399,
            'uniqid': 'LXKa4qnbur10',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '96975150,34394082,85468638',
            'value': '黑色,m,秋季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['96975150', '34394082', '85468638'],
              'value': ['黑色', 'm', '秋季']
            }
          },
          {
            'id': 400,
            'uniqid': 'PnXCuzfm1Kzz',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '96975150,34394082,80386662',
            'value': '黑色,m,夏季',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['96975150', '34394082', '80386662'],
              'value': ['黑色', 'm', '夏季']
            }
          },
          {
            'id': 401,
            'uniqid': 'Ljen54SvDXai',
            'retail_uniqid': null,
            'aid': null,
            'shop_item_id': 30,
            'key': '49660641,44220869,70473703',
            'key_value': '96975150,34394082,29551310',
            'value': '黑色,m,四季可穿',
            'specification': '',
            'sales': 0,
            'price': '99.00',
            'cost': '49.00',
            'marketprice': '159.00',
            'supply_price': '79.00',
            'stock': 999,
            'status': 1,
            'spec': {
              'key_id': ['49660641', '44220869', '70473703'],
              'value_id': ['96975150', '34394082', '29551310'],
              'value': ['黑色', 'm', '四季可穿']
            }
          }
        ],
        specData: [
          {
            'shop_item_id': 30,
            'key': '49660641',
            'key_name': '颜色',
            'value': [89392246, 96975150],
            'value_name': ['红色', '黑色'],
            'image': null,
            'store_id': 2
          },
          {
            'shop_item_id': 30,
            'key': '44220869',
            'key_name': '尺码',
            'value': [39096481, 34394082],
            'value_name': ['s', 'm'],
            'image': null,
            'store_id': 2
          },
          {
            'shop_item_id': 30,
            'key': '70473703',
            'key_name': '款式',
            'value': [85468638, 80386662, 29551310],
            'value_name': ['秋季', '夏季', '四季可穿'],
            'image': null,
            'store_id': 2
          }
        ]
      }
    },
    computed: {
      // 过滤sku列表，保留库存大于0的作为可选项
      skuList() {
        const data = []
        this.skuData.filter(item => item.stock > 0).forEach(item => {
          const option = {
            ...item,
            spec: item.spec.value.map((spec, index) => ({
              key_id: +item.spec.key_id[index],
              value_id: +item.spec.value_id[index],
              value: item.spec.value[index]
            }))
          }
          data.push(option)
        })
        return data
      },
      specList() {
        return this.specData.map(items => ({
          id: +items.key,
          value: items.key_name,
          spec: items.value.map((el, index) => ({
            id: +items.value[index],
            value: items.value_name[index]
          }))
        }))
      }
    },
    created() {
    },
    methods: {
      onSkuChange(res) {
        console.log(res)
      },
      onSkuSelect(res) {
        console.log(res)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .row {
    display: flex;
  }

  .label {
    height: 30px;
    line-height: 30px;
    font-size: 16px;
    color: #333333;
    width: 100px;
    text-align: right;
    padding: 10px 0;
    font-weight: bold;
  }

  .content {
    flex: 1;
    display: flex;
    flex-wrap: wrap;
  }

  .spec {
    min-width: 100px;
    height: 30px;
    line-height: 30px;
    border: 1px solid #dddddd;
    text-align: center;
    margin: 10px;
    border-radius: 4px;
    cursor: pointer;

    &:hover {
      border-color: #6c73e2;
      color: #6c73e2;
    }

    &_active {
      border-color: #6c73e2 !important;
      color: #ffffff !important;
      background: #6c73e2 !important;
    }

    &_disabled {
      border-color: #bdbdbd !important;
      color: #ffffff !important;
      background: #bdbdbd !important;
      cursor: not-allowed;
    }
  }
</style>
