<template>
  <div class="home">
    <div v-for="(item, itemIndex) in specList" :key="item.id" class="row">
      <div class="label">{{ item.value }}：</div>
      <div class="content">
        <div
          v-for="(spec, specIndex) in item.spec"
          :key="spec.id"
          class="spec"
          :class="{ 'spec_active' : spec.selected, 'spec_disabled': spec.disabled }"
          @click="handleSelectSpec(itemIndex, specIndex)"
        >
          {{ spec.value }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Home',
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
        ],
        selectedSpec: [],
        specList: [],
        hasSkuList: [], // 可用的sku例表
        valueIdSortAndIndex: []
      }
    },
    computed: {
      skuList() {
        const data = []
        this.skuData.forEach(item => {
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
      }
    },
    created() {
      this.init()
      this.getSpecList()
      this.initSpec()
    },
    methods: {
      init() {
        let valueIdSortAndIndex = [];
        this.hasSkuList = this.skuList.map((item) => {
          let valueIdSort = []
          item.spec.map(spec => {
            valueIdSort.push(spec.value_id)
          })
          /*将sku规格值的ID，组成一个数组并且字典排序，以及将该sku所对应的index存入数组，供点击后查询sku*/
          valueIdSortAndIndex.push({ valueIdSort: valueIdSort.sort() })
          return item.spec
        })
        this.valueIdSortAndIndex = valueIdSortAndIndex
      },
      // 初始化 判断 是否有库存
      initSpec() {
        let currentSkuList = this.hasSkuList.flat(Infinity) // 扁平化数组
        this.specList.forEach(items => {
          items.spec.forEach(item => {
            for (let i = 0, len = currentSkuList.length; i < len; i++) {
              if (item.id === currentSkuList[i].value_id) {
                item.disabled = false
                break
              }
            }
          })
        })
      },
      getSpecList() {
        const data = []
        this.specData.forEach(items => {
          const option = {
            id: +items.key,
            value: items.key_name,
            spec: items.value.map((el, index) => ({
              id: +items.value[index],
              value: items.value_name[index],
              selected: false,
              disabled: true
            }))
          }
          data.push(option)
        })
        this.specList = data
      },
      // 选择每个规格，判断对应的库存
      handleSelectSpec(rowIndex, colIndex) {
        let selectedList = this.selectedSpec // 已选规格
        const rowItem = this.specList[rowIndex]
        const colItem = rowItem.spec[colIndex]

        if (colItem.disabled) {
          return
        }

        // 处理selected的逻辑
        if (!colItem.selected) {
          this.specList[rowIndex].spec.forEach(item => {
            item.selected = false
          })
          this.specList[rowIndex].spec[colIndex].selected = true
          // 选中项中有同组元素，替换
          selectedList.forEach((item, index) => {
            if (item.rowIndex === rowIndex) {
              selectedList.splice(index, 1)
            }
          })
          selectedList.push({ rowId: rowItem.id, colId: colItem.id, rowIndex, colIndex })
        } else {
          // 取消选中并删除选中项中数据
          this.specList[rowIndex].spec[colIndex].selected = false
          selectedList.forEach((item, index) => {
            if (item.colId === colItem.id && item.rowId === rowItem.id) {
              selectedList.splice(index, 1)
            }
          })
        }

        // 取出行的ID
        const selectedRowIds = selectedList.map(item => item.rowId)

        // 处理disabled的逻辑
        if (selectedList.length === 0) {
          // 选中属性为空，重新初始化数据
          this.initSpec()
        } else {
          //拿所有规格属性（即specList）的每一项分别与已选中的数据（即selectItemList）的每一项，组成一个比较项，与现有库存比较，找到存在的可点项
          this.specList.forEach((row, rowIndex) => {
            row.spec.forEach((col, colIndex) => {
              // 将没有选择的规格全部设置为禁用
              if (!col.selected) {
                col.disabled = true
              }
              // 本次循环数据
              let pushData = { rowId: row.id, colId: col.id, rowIndex: rowIndex, colIndex: colIndex }
              if (selectedRowIds.indexOf(row.id) > -1) {
                // 当前循环的规格的组ID在已选规格中，删除同组规格，用当前规格替换后去与库存比较
                const sel = selectedList.slice() // 用一个新变量接受数据，防止修改源数据
                const indexSplice = selectedRowIds.indexOf(row.id)
                sel.splice(indexSplice, 1, pushData)
                this.optionsHandle(sel, pushData)
              } else {
                //  当前循环规格组ID不在已选规格中，添加当前规格到复制出来的已选数组中，循环比较
                const sel = selectedList.slice()
                sel.push(pushData)
                this.optionsHandle(sel, pushData)
              }
            })
          })
        }
      },
      optionsHandle(colArr, pushData) {
        // 将当前比较项的属性ID提取
        const colIds = colArr.map(item => item.colId)
        // 在现有库存中查找是否有可选项，可选的置为可点击
        this.valueIdSortAndIndex.map(item => {
          if (this.isContained(item.valueIdSort, colIds)) {
            this.specList[pushData.rowIndex].spec[pushData.colIndex].disabled = false
          }
        })
      },
      /*
      * 判断arr1数组是否 全 包含arr2数组
      * */
      isContained(arr1, arr2) {
        if(!(arr1 instanceof Array) || !(arr2 instanceof Array) || (arr1.length < arr2.length)) {
          return false
        }
        let arr1Str = arr1.toString()
        for (let i = 0, len = arr2.length; i < len; i++) {
          if (arr1Str.indexOf(arr2[i]) < 0) {
            return false
          }
        }
        return true
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
