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
    name: 'Sku',
    props: {
      skuData: {
        type: Array,
        default: () => []
      },
      specData: {
        type: Array,
        default: () => []
      }
    },
    data() {
      return {
        selectedSpec: [], // 已选的规格
        specList: [], // 规格列表
        hasSkuList: [], // 可用的sku例表
        valueIdSortAndIndex: []
      }
    },
    computed: {
      // 获取库存大于0的sku列表
      skuList() {
        const data = this.skuData.map(item => ({
          ...item,
          ids: item.spec.map((item) => {
            return item.value_id
          }).sort((a, b) => {
            return a - b
          }).toString()
        }))
        return data
      }
    },
    watch: {
      specData: {
        deep: true,
        handler() {
          this.initSpec()
        }
      },
      skuList: {
        deep: true,
        handler() {
          this.init()
          this.initSpec()
        }
      }
    },
    created() {
      this.init()
      this.initSpec()
    },
    methods: {
      init() {
        let valueIdSortAndIndex = []
        this.hasSkuList = this.skuList.map((item, index) => {
          let valueIdSort = []
          item.spec.map(spec => {
            valueIdSort.push(spec.value_id)
          })
          /* 将sku规格值的ID，组成一个数组并且字典排序，以及将该sku所对应的index存入数组，供点击后查询sku */
          valueIdSortAndIndex.push({ valueIdSort: valueIdSort.sort() })
          return item.spec
        })
        this.valueIdSortAndIndex = valueIdSortAndIndex
      },
      // 初始化 判断 是否有库存
      initSpecStatus() {
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
      // 初始化规格列表的选中项
      initSpec() {
        const data = []
        this.specData.forEach(items => {
          const option = {
            ...items,
            spec: items.spec.map((el, index) => ({
              ...el,
              selected: false,
              disabled: true
            }))
          }
          data.push(option)
        })
        this.specList = data

        this.initSpecStatus()
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
                // 当前循环规格组ID不在已选规格中，添加当前规格到复制出来的已选数组中，循环比较
                const sel = selectedList.slice()
                sel.push(pushData)
                this.optionsHandle(sel, pushData)
              }
            })
          })
        }
        this.onChange()
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
      },
      findSku(specIds = []) {
        const data = []
        const selectedIds = specIds.sort((a, b) => a - b).toString()
        for (const key in this.skuList) {
          if (this.skuList[key].ids.indexOf(selectedIds) > -1) {
            data.push(this.skuList[key])
          }
        }
        return data
      },
      getCurrentSped(specData = this.selectedSpec) {
        const data = []
        specData.forEach(spec => {
          const option = {}
          this.specList.forEach(row => {
            if (row.id === spec.rowId) {
              option.k_id = row.id
              option.k_value = row.value
            }
            row.spec.forEach((col) => {
              if (col.id === spec.colId) {
                option.v_id = col.id
                option.v_value = col.value
              }
            })
          })
          data.push(option)
        })
        return data
      },
      onChange() {
        const selectedIds = this.selectedSpec.map(item => item.colId)
        const currentSpec = this.getCurrentSped() // 当前选中的规格
        if ((selectedIds && selectedIds.length) >= this.specList.length) {
          const data = this.findSku(selectedIds)
          this.$emit('on-select', (data && data.length) && data[0])
        }
        this.$emit('on-change', currentSpec)
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
