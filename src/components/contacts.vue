<template>
  <div class="contacts">
    <table-component
      @changePage="getCameraData($event.limit, $event.offset, $event.sort)"
      :showCheckbox="false"
      :showSearch="false"
      :tableData="tableDataFormated"
      :columns="columnsReesterTable"
      :paginatorInputData="tablePaginator"/>
  </div>
</template>

<script>
import table from '@/components/common/table'
export default {
  name: 'contacts',
  components: {
    'table-component': table
  },
  data () {
    return {
      tableDataFormated: [{id: 1, name: 'test', cam_type: 'type', district: 'district'}],
      columnsReesterTable: [
        {name: '№', code: '-id'},
        {name: 'Наименование', code: '-name'},
        {name: 'Тип', code: '-camera_type__name'},
        {name: 'Адрес', code: '-address__full_address'},
        {name: 'Район', code: '-address__district'}
      ],
      tablePaginator: {
        count: 777,
        next: 'url',
        previous: 'url_2'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

</style>
