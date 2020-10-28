<template>
  <div>
    <div class="content fix-header fix-bottom">
      <!--      弹出层 选择商品规格-->
      <div class="mask">
        <div class="mask-content">
          <div class="mask-title">
            <div class="mask-close iconfont-shop icon-close"></div>
            选择规格参数
          </div>
          <div class="spec-items">
            <div class="row" v-for="(item, index) in goodsTypeList" :key="item.id">
              <div class="label">{{item.name}}</div>
              <div class="content">
                <span v-for="(el, i) in item.propertyList"
                      :key="el.id"
                      class="spec"
                      :class="{'spec_active' : el.selected, 'spec_disabled': el.disabled}"
                      @click="handleClickSpecs1(item.id, el.id, el, index, i)"
                >{{el.name}}</span>
              </div>
            </div>
            <div class="spec-menu-item">
              <div class="spec-note">数量</div>
              <div class="spec-num">
                <span class="minus">-</span>
                <input type="number" v-model="buyNumber" maxlength="3"/>
                <span class="add">+</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  let orgdata = {
    "skus": [
      {
        "id": "f5eee18b8d5b4fc2b46a56e92abdb525",
        "stockAmmount": 7,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "74fe546803e44a7c95bebfe56a29952d",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "f40c3884e5e9422c973d31631a65ae64",
            "propertyName": "小",
            "property": 1
          },
          {
            "id": "78f98ee53ae549ceb2c18629152ff849",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "02808ac287e8410f936a90167d82ee2b",
            "propertyName": "two",
            "property": 2
          },
          {
            "id": "91cefe600f40498bb5013deebb9c27be",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          }
        ]
      },
      {
        "id": "383feb7947f14ce5b832bc8700e65c9e",
        "stockAmmount": 2,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "1beed60c2eb244f89ad82806d343d468",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "02808ac287e8410f936a90167d82ee2b",
            "propertyName": "two",
            "property": 2
          },
          {
            "id": "357fd7db1f5244e5b64f48a34bb581fa",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "edac997ed2c54e41b1f3076fbd6e19f9",
            "propertyName": "中",
            "property": 2
          },
          {
            "id": "5c29a251e55a4b678fc4f8287cc560b5",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          }
        ]
      },
      {
        "id": "905b10e1740e4be992d14cfc23a887a2",
        "stockAmmount": 4,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "0a5f93d9ef1c486ba369dcb1fbd3aed9",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "c76dc797eaae4d8eb360de8811a9ec7a",
            "propertyName": "one",
            "property": 1
          },
          {
            "id": "d920730c34644218b3d0bbc5fca5edf4",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "f40c3884e5e9422c973d31631a65ae64",
            "propertyName": "小",
            "property": 1
          },
          {
            "id": "2afbe8a77d034de0a1655f9ad1a25b95",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          }
        ]
      },
      {
        "id": "a440b0084e564d3e9d7c8b445bb7645e",
        "stockAmmount": 10,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "12a4715b6730438888e88f302871245a",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "f40c3884e5e9422c973d31631a65ae64",
            "propertyName": "小",
            "property": 1
          },
          {
            "id": "9063e1f1586f4a74b2f614039e8743c4",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          },
          {
            "id": "ae38b9cf56d5408a809d6fbd1b902ee5",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "d5660085ff8743d999f6ed3a497ec8b7",
            "propertyName": "three",
            "property": 3
          }
        ]
      },
      {
        "id": "9961364cc3494823aaf7699733393335",
        "stockAmmount": 15,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "3335920f79914cfb8a39ae22b0802bc0",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "c76dc797eaae4d8eb360de8811a9ec7a",
            "propertyName": "one",
            "property": 1
          },
          {
            "id": "34950de7059d4fffac485abb59a79381",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "edac997ed2c54e41b1f3076fbd6e19f9",
            "propertyName": "中",
            "property": 2
          },
          {
            "id": "a82ff8d74d3d4a1ea454e4870cc68b64",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          }
        ]
      },
      {
        "id": "bd3aeb3c7c854a80b88e7f82a5a78a1e",
        "stockAmmount": 8,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "4fc8e61aa192463085578de92974b18b",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "edac997ed2c54e41b1f3076fbd6e19f9",
            "propertyName": "中",
            "property": 2
          },
          {
            "id": "884f32b64a4b478bb01f93b40dfeb6fc",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          },
          {
            "id": "f66109eccd934529a18026376fccfa7b",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "d5660085ff8743d999f6ed3a497ec8b7",
            "propertyName": "three",
            "property": 3
          }
        ]
      },
      {
        "id": "5e094973bbaf41ce81b7b626174b0bbf",
        "stockAmmount": 8,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "23d688678aaa42eebd3c04cceaa61bac",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "8ed34030c93c4dc29e43edb95e6cfca2",
            "propertyName": "橙色",
            "property": 1
          },
          {
            "id": "55649f0753464921b68b0017ce0010d7",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "408fb530344a4a41b33932431638dcbb",
            "propertyName": "大",
            "property": 3
          },
          {
            "id": "d7248b12b7e847ca9be024ed3bb6d101",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "d5660085ff8743d999f6ed3a497ec8b7",
            "propertyName": "three",
            "property": 3
          }
        ]
      },
      {
        "id": "60ce0a1f99e940dc82d041d36681111b",
        "stockAmmount": 9,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "91faddf91e944cabadbda5c342430139",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          },
          {
            "id": "207698d97e4247bb9747843d16e25750",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "408fb530344a4a41b33932431638dcbb",
            "propertyName": "大",
            "property": 3
          },
          {
            "id": "3c69d3c73aa24cccbacaf805d71117fd",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "d5660085ff8743d999f6ed3a497ec8b7",
            "propertyName": "three",
            "property": 3
          }
        ]
      },
      {
        "id": "f3c805d1959d413a86679955ae047ec5",
        "stockAmmount": 10,
        "isPaymentAccpoints": 1,
        "isPaymentCurrency": 0,
        "isPaymentMixed": 0,
        "priceAccpoints": 1,
        "priceCurrency": 0,
        "mixedPriceAccpoints": 0,
        "mixedPriceCurrency": 0,
        "rebate": 100,
        "skusTypes": [
          {
            "id": "00113d4b6046411cb8ff935b2743904b",
            "typeId": "fe7f49a798794670be622e6b9d2f386a",
            "typeName": "tester",
            "type": 3,
            "propertyId": "02808ac287e8410f936a90167d82ee2b",
            "propertyName": "two",
            "property": 2
          },
          {
            "id": "c13d8a4c7a18477fbe7027044d0393a0",
            "typeId": "547f76222d4d4f92a49de2e0bf6bd7ef",
            "typeName": "颜色",
            "type": 1,
            "propertyId": "c80cbe4c6cbf49f5b2822331768cd422",
            "propertyName": "绿色",
            "property": 2
          },
          {
            "id": "653d0e243bab45eaa5c83dc8206ee33e",
            "typeId": "21967fba6b574b479974e50720ad25fe",
            "typeName": "测试类别",
            "type": 2,
            "propertyId": "408fb530344a4a41b33932431638dcbb",
            "propertyName": "大",
            "property": 3
          }
        ]
      }
    ]
  };
  let goodType = [
    {
      "id": "547f76222d4d4f92a49de2e0bf6bd7ef",
      "type": 1,
      "name": "颜色",
      "propertyList": [
        {
          "id": "8ed34030c93c4dc29e43edb95e6cfca2",
          "property": 1,
          "name": "橙色"
        },
        {
          "id": "c80cbe4c6cbf49f5b2822331768cd422",
          "property": 2,
          "name": "绿色"
        }
      ]
    },
    {
      "id": "21967fba6b574b479974e50720ad25fe",
      "type": 2,
      "name": "测试类别",
      "propertyList": [
        {
          "id": "f40c3884e5e9422c973d31631a65ae64",
          "property": 1,
          "name": "小"
        },
        {
          "id": "edac997ed2c54e41b1f3076fbd6e19f9",
          "property": 2,
          "name": "中"
        }
      ]
    },
    {
      "id": "fe7f49a798794670be622e6b9d2f386a",
      "type": 3,
      "name": "tester",
      "propertyList": [
        {
          "id": "c76dc797eaae4d8eb360de8811a9ec7a",
          "property": 1,
          "name": "one"
        },
        {
          "id": "02808ac287e8410f936a90167d82ee2b",
          "property": 2,
          "name": "two"
        },
        {
          "id": "d5660085ff8743d999f6ed3a497ec8b7",
          "property": 3,
          "name": "three"
        }
      ]
    }
  ]

  export default {
    name: "Detail",
    data() {
      return {
        maskVisible: true,
        skuList: [],
        lastCheckedSku: {}, // 选中的sku信息
        buyNumber: 1, // 购买数量
        sku: null,
        currentSkuList: [],
        valueIdSortAndIndex: [],
        goodsTypeList: [],
        selectItemList: []
      }
    },
    mounted() {
      this.init();
      // 获取所有的规格
      this.getShopGoodsType()
      this.initGoodType()
    },
    methods: {
      init() {
        let valueIdSortAndIndex = [];
        let currentSkuList = orgdata.skus.map((item,index) => {
          let valueIdSort = [];
          item.skusTypes.map(skusTypesItem=>{
            valueIdSort.push(skusTypesItem.propertyId)
          });
          console.log(index)
          // console.log(valueIdSort)
          /*
           将sku规格值的ID，即 propertyId，组成一个数组并且字典排序，以及将该sku所对应的index存入数组，供点击后查询sku*/
          valueIdSortAndIndex.push({valueIdSort: valueIdSort.sort()})
          return item.skusTypes
        });

        console.log(valueIdSortAndIndex)

        this.$set(this.$data, 'currentSkuList', currentSkuList);
        this.$set(this.$data, 'valueIdSortAndIndex', valueIdSortAndIndex);
      
      },
      
      isContained(aa, bb) {
        //判断aa数组是否 全 包含bb数组
        if(!(aa instanceof Array)
            ||!(bb instanceof Array)
            ||(aa.length<bb.length)
        ){
          return false;
        }
        let aaStr = aa.toString();
        for(var i=0;i<bb.length;i++){
          if(aaStr.indexOf(bb[i])<0){
            return false;
          }
        }
        return true;
      },
      // 获取所有的规格
      getShopGoodsType() {
        // goodType 为接口返回数据
        goodType.forEach(items=>{
          items.propertyList.forEach(item=>{
            item.selected = false;
            item.disabled = true;
          })
        })
        this.goodsTypeList = goodType;
      },
      // 初始化 判断 是否有库存
      initGoodType(){
        let currentSkuList = this.currentSkuList.flat(Infinity);
        this.goodsTypeList.forEach(items=>{
          items.propertyList.forEach(item=>{
            for(var i=0; i<currentSkuList.length; i++){
              if (item.id == currentSkuList[i].propertyId) {
                item.disabled = false;
                break;
              }
            }
          })
        })
      },
      // 选择每个规格，判断对应的库存
      handleClickSpecs1(grounpId, id, el, index, i){
        let selectItemList = this.selectItemList; // 已选规格

        if (el.disabled) {
          return;
        }
        // 处理selected的逻辑
        if (!el.selected) {
          this.goodsTypeList[index].propertyList.forEach(item=>{
            item.selected = false;
          })
          this.goodsTypeList[index].propertyList[i].selected = true;
          // 选中项中有同组元素，替换
          selectItemList.forEach((item, x_selected_index) => {
            if (item.index === index) {
              selectItemList.splice(x_selected_index, 1)
            }
          });
          selectItemList.push({grounpId, id, index, i});
        } else  {
          // 取消选中并删除选中项中数据
          this.goodsTypeList[index].propertyList[i].selected = false;
          selectItemList.forEach((item, x_selected_index) => {
            if (item.id === id && item.grounpId === grounpId) {
              selectItemList.splice(x_selected_index, 1);
            }
          });
        }
        this.$set(this.$data, 'selectItemList', selectItemList)

        // 取出组ID
        let x_selected_grounpIds = [];
        selectItemList.forEach(item=>{
          x_selected_grounpIds.push(item.grounpId);
        });

        // 处理disabled的逻辑
        if (selectItemList.length == 0) {
          // 选中属性为空，重新初始化数据
          this.initGoodType();
        } else {
          //拿所有规格属性（即goodsTypeList）的每一项分别与已选中的数据（即selectItemList）的每一项，组成一个比较项，与现有库存比较，找到存在的可点项
          this.goodsTypeList.forEach((goodsType,goodsTypeIndex)=>{
            goodsType.propertyList.forEach((prop, propIndex)=>{
              if (!prop.selected) {
                prop.disabled = true;
              }
              // 本次循环数据
              let push_data = {grounpId: goodsType.id, id: prop.id, index: goodsTypeIndex, i: propIndex}
              // console.log(x_selected_grounpIds, goodsType)
              if (x_selected_grounpIds.indexOf(goodsType.id) > -1 ){
                // 当前循环的规格的组ID在已选规格中，删除同组规格，用当前规格替换后去与库存比较
                let sel = selectItemList.slice(); // 用一个新变量接受数据，防止修改源数据
                let index_splice = x_selected_grounpIds.indexOf(goodsType.id);
                sel.splice(index_splice, 1, push_data);
                this.optionsHandle(sel, push_data)
              } else {
              //  当前循环规格组ID不在已选规格中，添加当前规格到复制出来的已选数组中，循环比较
                let sel = selectItemList.slice();
                sel.push(push_data);
                this.optionsHandle(sel, push_data)
              }
            })
          })
        }
      },
      optionsHandle(selArr, push_data){
        let propertyIds = []
        // 将当前比较项的属性ID提取
        selArr.map(item=>{
          propertyIds.push(item.id)
        });
        // 在现有库存中查找是否有可选项，可选的置为可点击
        console.log(this.valueIdSortAndIndex)
        this.valueIdSortAndIndex.map(item=>{
          if (this.isContained(item.valueIdSort, propertyIds)){
            this.goodsTypeList[push_data.index].propertyList[push_data.i].disabled = false;
          }
        });
      }
    }
  };
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
