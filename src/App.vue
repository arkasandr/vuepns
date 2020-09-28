<template>
  <div id="service_name">
"Обрабтка данных ПСН"
  </div>
</template>
  <template>
  <div>
    <vue-table-dynamic
            :params="params"
            @select="onSelect"
            @selection-change="onSelectionChange"
            ref="table"
    >
    </vue-table-dynamic>
  </div>
</template>

<script>
  import VueTableDynamic from 'vue-table-dynamic'
  export default {
    name: 'Demo',
    data() {
      return {
        params: {
          data: [
            ['Дата загрузки', 'Полученный архив', 'Обработанный архив', 'Статус'],
            ['23.09.2020', '20200910_DEPRMPSN_2016', '20200910_DEPRMPSNv2_2016', 'Готов'],
            ['24.09.2020', '20200910_DEPRMPSN_2017', '', 'Загружен'],
            ['04.10.2020', '20200910_DEPRMPSN_2018', '', 'Обработан'],
            ['11.10.2020', '20200910_DEPRMPSN_2019', '', 'Готов']
          ],
          header: 'row',
          sort: [0, 3],
          border: true,
          columnWidth: [{column: 0, width: '20%'}, {column: 1, width: '30%'}, {column: 2, width: '20%'}, {column: 3, width: '20%'}, {column: 4, width: '20%'}],
          showCheck: true,
          stripe: true,
          height: 180
        }
      }
    },
    methods: {
      onSelect (isChecked, index, data) {
        console.log('onSelect: ', isChecked, index, data)
        console.log('Checked Data:', this.$refs.table.getCheckedRowDatas(true))
      },
      onSelectionChange (checkedDatas, checkedIndexs, checkedNum) {
        console.log('onSelectionChange: ', checkedDatas, checkedIndexs, checkedNum)
      }
    },
    components: { VueTableDynamic }
  }
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'
</script>

<style>

</style>
