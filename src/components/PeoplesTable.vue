<template>
  <div class="wrapper">
    <div class="table" style="overfolw: hidden; width: 100%">
      <hot-table licenseKey="non-commercial-and-evaluation" ref="hotTableComponent" :settings="hotSettings">
      </hot-table>
    </div>
    <div class="buttons_block">
      <button @click="recieveData" class="people_btn">загрузить с сервера</button>
      <button class="people_btn">загрузить на сервер</button>
      <button class="people_btn">скачать в .xls</button>
    </div>
  </div>
  
</template>

<script>
import { HotTable, HotColumn } from "@handsontable/vue";
import Handsontable from 'handsontable';

export default {
  name: "PeoplesTable",
  components: {
    HotTable,
    HotColumn,
  },
  data: function() {
    return {
      dataObject: {},
      hotSettings: {
        rowHeaders: true,
        columns: [
          { data: 'name', type: 'text' }, { data: 'username', type: 'text' }, { data: 'email', type: 'text' },
          { data: 'phone',  type: 'text' }, { data: 'website', type: 'text' }, {  data: 'company.name', type: 'text' },
          { data: 'company.catchPhrase',  type: 'text' }, { data: 'company.bs', type: 'text' }, { data: 'address.city', type: 'text' },
          { data: 'address.street', type: 'text' }, { data: 'address.suite', type: 'text' }, 
          { data: 'address.zipcode', type: 'text' }, 
        ],
        stretchH: 'all',
        width: "100%",
        autoWrapRow: true,
        height: 487,
        maxRows: 6,
        colHeaders: [
          'Name',
          'Username',
          'Email',
          'Phone',
          'Website',
          'Company Name',
          'Catch Phrase',
          'BS',
          'City',
          'Street',
          'Suite',
          'Zipcode'
        ]
      },
    }
  },
  methods: {
    recieveData: function() {
      this.axios.get('https://jsonplaceholder.typicode.com/users').then((response) => {
        console.log( response.data);
        var data = response.data;
        this.$refs.hotTableComponent.hotInstance.loadData(data);
      })
    }
  }
};
</script>

<style lang="less">
  .ht_clone_top,
  .ht_clone_bottom,
  .ht_clone_left {
    display: none;
  }
  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    height: 100%;
  }
  
  table {
    width: 100%;
    border: 1px solid #E5E5E5 !important;
    height: 400px;
  }
  .wtHolder {
      height: fit-content !important;
      }
  .wtHider {
    width: 94% !important;
  }
  @media (min-width: 569px) {
    .buttons_block {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
      align-items: center;
      margin-left: 32px;
      width: 100%;
      height: 150px;
      flex-wrap: wrap;
      .people_btn {
        width: 255px;
        height: 46px;
        background: #86764B;
        border-radius: 4px;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        outline: none;
        border: none;
        font-family: Roboto;
        font-style: normal;
        font-weight: bold;
        text-transform: uppercase;
        color: #ffffff;
        margin: 0 20px 0px 0;
      }
      .people_btn:hover {
        background-color: #424242;
      }
      .people_btn:active {
        background-color: #000000;
      }
    }
  }
</style>