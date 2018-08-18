<template>
  <v-card class="currency-stat-card">
    <v-layout row wrap>
      <v-flex md3 sm12 xs12>
        <p class="csc-main-heading">BTC-ADA</p>
        <p class="csc-secondary-heading">Ada</p>
      </v-flex>
      <v-flex md9 :class="checkWidth ? 'csc-right-flex' : 'csc-right-flex-responsive'">
        <v-layout row wrap class="csc-right-layout">
          <v-flex xs6 sm6 md2 v-for="item in currencyStatsItems" :key="item.title" class="csc-right-inner-flex">
            <p>$ {{item.topCurrency}}</p>
            <p>$ {{item.midCurrency}}</p>
            <p :class="item.title === 'ASK' ? 'loss' : 'profit'">{{item.title}}</p>
          </v-flex>
          <v-flex xs6 sm6 md2 v-for="(item, index) in dailyCurrencyStatsItems" :key="index" class="csc-right-inner-flex">
            <p>$ {{item.topCurrency}}</p>
            <p>$ {{item.midCurrency}}</p>
            <p>{{item.title}}</p>
          </v-flex>
        </v-layout>
      </v-flex>
    </v-layout>
  </v-card>
</template>
<script>
export default {
  props: ['checkWidth'],
  data () {
    return {
      currencyStatsItems: [
        {
          topCurrency: '0.14',
          midCurrency: '0.0002138',
          title: 'LAST'
        },
        {
          topCurrency: '0.14',
          midCurrency: '0.0002132',
          title: 'BID'
        },
        {
          topCurrency: '0.14',
          midCurrency: '0.0002255',
          title: 'ASK'
        },
        {
          topCurrency: '4035284.17',
          midCurrency: '639.38000000',
          title: 'VOLUME'
        }
      ],
      dailyCurrencyStatsItems: [
        {
          topCurrency: '0.14',
          midCurrency: '0.00002140',
          title: '24H HIGH'
        },
        {
          topCurrency: '0.12',
          midCurrency: '0.00001926',
          title: '24H LOW'
        }
      ]
    }
  }
}
</script>

<style scoped>
p {
  margin: 0px;
  color: white;
}
.currency-stat-card {
  background-color: #4E5464;
}
.csc-main-heading {
  font-size: 34px;
  padding-left: 15px;
}
.csc-secondary-heading {
  font-size: 24px;
  padding-left: 15px;
}
.csc-right-flex {
  text-align: right;
  padding-right: 15px;
  padding-top: 15px
}
.csc-right-flex-responsive {
  padding-left: 15px;
}
.csc-right-flex-responsive .csc-right-inner-flex {
  padding-bottom: 20px !important;
}
.csc-right-layout p{
  font-size: 12px;
  vertical-align: middle;
}
.profit {
  color: springgreen
}
.loss {
  color: #985567
}
</style>
