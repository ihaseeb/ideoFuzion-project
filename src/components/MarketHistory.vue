<template>
  <data-tables :data='tableData' :table-props="tableProps" style="width: auto" max-height="50" class="data-table">
      <el-table-column
        prop="sum"
        label="SUM"
        width="auto">
      </el-table-column>
      <el-table-column
        prop="total"
        label="TOTAL"
        width="auto">
      </el-table-column>
      <el-table-column
        prop="size"
        label="SIZE(ADA)"
        width="auto">
      </el-table-column>
      <el-table-column
        prop="bid"
        label="BID(BTC)"
        width="auto">
      </el-table-column>
      <el-table-column
        prop="status"
        label=""
        width="auto">
      </el-table-column>
    
    </data-tables>
</template>
<script>
export default {
  data () {
    return {
      tableProps: {
        border: true,
        stripe: true
      },
      titles: [
        {
          label: 'SUM',
          prop: 'sum'
        },
        {
          label: 'Total',
          prop: 'total'
        },
        {
          label: 'SIZE(ADA)',
          prop: 'size'
        },
        {
          label: 'BID(BTC)',
          prop: 'bid'
        },
        {
          label: '',
          prop: 'status'
        }
      ],
      tableData: [
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          bid: '0.00002125',
          status: 'SELL'
        }
      ]
    }
  }
}
</script>
<style scoped>
.data-table {
  background-color: #4E5464 !important;
}
</style>
