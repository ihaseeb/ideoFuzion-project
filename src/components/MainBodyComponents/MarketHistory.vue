<template>
  <v-data-table
    :headers="titles"
    :items="tableData"
    :pagination.sync="pagination"
    item-key="name"
    :rows-per-page-items='rowsPerPage'
    dark
    class="elevation-1 data-table"
  >
    <template slot="headers" slot-scope="props">
      <tr class="table-row-heading">
        <th
          v-for="header in props.headers"
          :key="header.label"
        >
          {{ header.label }}
        </th>
      </tr>
    </template>
    <template slot="items" slot-scope="props" >
      <tr class="table-row" :class="checkRow(props.index) ? 'table-row-strip' : 'table-row-simple'">
        <td>{{ props.item.date }}</td>
        <td :class="props.item.status === 'SELL' ? 'loss' : 'profit'">{{ props.item.status }}</td>
        <td>{{ props.item.bidAsk }}</td>
        <td>{{ props.item.totalUnit }}</td>
        <td>{{ props.item.totalCost }}</td>
      </tr>
    </template>
  </v-data-table>
</template>
<script>
  export default {
    props: ['titles', 'tableData'],
    data: () => ({
      rowsPerPage: [5, 10, 25, {'text': '$vuetify.dataIterator.rowsPerPageAll', 'value': -1}],
      pagination: {
        sortBy: 'name'
      }
    }),

    methods: {
      toggleAll () {
        if (this.selected.length) this.selected = []
        else this.selected = this.desserts.slice()
      },
      changeSort (column) {
        if (this.pagination.sortBy === column) {
          this.pagination.descending = !this.pagination.descending
        } else {
          this.pagination.sortBy = column
          this.pagination.descending = false
        }
      },
      checkRow (data) {
        if (data % 2 === 0 || data === 0) {
          return true
        } else {
          return false
        }
      }
    }
  }
</script>
<style scoped>
.data-table {
  color: #f1f1f1
}
th {
  text-align: left
}
td {
  text-align: left
}
.data-table /deep/ .v-datatable__actions {
  background-color: #4E5464 !important;
}
.data-table /deep/ .table-row {
  background-color: #4E5464;
}
.data-table /deep/ .table-row-strip {
  background-color: #424856 ;
}
.data-table /deep/ .table-row-simple {
  background-color: #4E5464 ;
}
.table-row-heading {
  background-color: #4E5464 !important;
}
.data-table /deep/ .loss {
  color: rgb(207, 60, 85)
}
.data-table /deep/ .profit {
  color: springgreen
}
</style>
