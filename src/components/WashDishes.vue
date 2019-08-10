<template>
  <div>
    <group>
      <cell :title="$t('洗碗队列')"></cell>
      <cell-form-preview :list="list"></cell-form-preview>
    </group>

    <divider>{{ $t('吃饭人员') }}</divider>
    <div class="box">
      <checker v-model="demo1Checkbox" type="checkbox" default-item-class="demo1-item" selected-item-class="demo1-item-selected">
        <checker-item :value="1">{{ $t('雷') }}</checker-item>
        <checker-item :value="2">{{ $t('洪') }}</checker-item>
        <checker-item :value="3">{{ $t('吴') }}</checker-item>
        <checker-item :value="4">{{ $t('邓') }}</checker-item>
        <checker-item :value="5">{{ $t('黄') }}</checker-item>
        <checker-item :value="6">{{ $t('龙') }}</checker-item>
        <checker-item :value="7">{{ $t('贾') }}</checker-item>
      </checker>
      <br>
      <span>{{ $t('Current value is') }}: {{demo1Checkbox}}</span>
      <br>
    </div>
    <checker v-model="demo6" type="checkbox" default-item-class="demo5-item" selected-item-class="demo5-item-selected">
      <checker-item v-for="i in [1, 2, 3,4,5,6,7]" :key="i" :value="i">{{['雷', '邓','洪','黄','龙','贾','吴'][i - 1]}}</checker-item>
    </checker>
    <divider>{{ $t('做饭人员') }} {{demo6}}</divider>

    <group style="padding-top: 20px;">
      <x-switch :title="$t('查看谁洗碗')" v-model="show7"></x-switch>
    </group>
    <actionsheet v-model="show7" :menus="menu7" theme="android" @on-click-menu="click" @on-after-hide="log('after hide')"
      @on-after-show="log('after show')">
    </actionsheet>
  </div>
</template>

<script>
  import {
    CellFormPreview,
    Group,
    Cell,
    Checker,
    CheckerItem,
    TransferDom,
    Actionsheet,
    XSwitch,
    Toast
  } from 'vux'
  export default {
    components: {
      CellFormPreview,
      Group,
      Cell,
      Checker,
      CheckerItem,
      TransferDom,
      Actionsheet,
      XSwitch,
      Toast
    },
    methods: {
      log(str) {
        console.log(str)
      },
       click (key) {
      console.log(key)
    },
    },
    data() {
      return {
        list: [{
          label: '王雷',
          value: '7'
        }, {
          label: '邓鑫',
          value: '14'
        }, {
          label: '洪飞',
          value: '21'
        }],
        demo1Checkbox: [2, 1],
        demo6: [2, 3],
        show7: false,
        menu7: {
          menu1: '王雷',
        },
      }
    }
  }
</script>
<style scoped>
  .box {
    padding: 0 15px;
  }

  .demo1-item {
    width: 70px;
    border: 1px solid #ececec;
    padding: 5px 15px;
  }

  .demo1-item-selected {
    border: 2px solid green;
  }

  .demo5-item {
    width: 70px;
    height: 26px;
    line-height: 26px;
    text-align: center;
    border-radius: 3px;
    border: 1px solid #ccc;
    background-color: #fff;
    margin-right: 6px;
  }

  .demo5-item-selected {
    background: #ffffff url(../assets/active.png) no-repeat right bottom;
    border-color: #ff4a00;
  }
</style>
