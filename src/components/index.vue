<template>
  <v-container fluid>
    <v-layout row wrap>
      <v-flex md12>
        <currency-stats-items :checkWidth=checkWidth></currency-stats-items>
      </v-flex>
    </v-layout>
    <v-layout row wrap class="mt-4">
      <v-flex md12>
        <empty-card></empty-card>
      </v-flex>
    </v-layout>
    <v-layout row wrap class="mt-4">
      <v-flex  md4 sm12 xs12 class="eth-cards" v-for="(card, i) in ethCards" :key="i" :class="i !== 2 && checkWidth? 'eth-cards-special' : 'eth-cards-special-responsive'">
        <buy-eth-card
          :windowWidth='windowWidth'
          :bitCoins='card.bitCoins'
          :lowestAsk='card.lowestAsk'
          :price='card.price'
          :feeValue='card.feeValue'
          :mainHeading='card.mainHeading'
          :secondaryHeading='card.secondaryHeading'
          :total='card.total'></buy-eth-card>
      </v-flex>
    </v-layout>
    <v-layout row wrap class="mt-4">
      <v-flex md12>
        <v-card class="table-card">
            <v-card-title class="table-card-title">ORDER BOOK</v-card-title>
          <v-layout row wrap>
            <v-flex md6>
              <order-book :titles='titlesLeft' :tableData='tableDataLeft'></order-book>
            </v-flex>
            <v-flex md6>
              <order-book :titles='titlesRight' :tableData='tableDataRight'></order-book>
            </v-flex>
          </v-layout>
        </v-card>
      </v-flex>
    </v-layout>
    <v-layout row wrap class="mt-4">
      <v-flex md12>
        <v-card class="table-card">
          <v-card-title class="table-card-title">MARKET HISTORY</v-card-title>
            <v-layout row wrap>
              <v-flex md12>
                <market-history :titles='marketTitles' :tableData='marketData'></market-history>
              </v-flex>
            </v-layout>
          </v-card>
      </v-flex>
    </v-layout>
    <v-layout row wrap class="mt-4">
      <v-flex md12>
        <v-card class="table-card">
          <v-card-title class="table-card-title">MY OPEN ORDERS</v-card-title>
          </v-card>
      </v-flex>
    </v-layout>
    <v-layout row wrap class="mt-4">
      <v-flex md12>
        <v-card class="table-card">
          <v-card-title class="table-card-title">MY ORDER HISTORY</v-card-title>
          </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import CurrencyStatsItems from '@/components/MainBodyComponents/CurrencyStatComponent.vue'
import EmptyCard from '@/components/MainBodyComponents/emptyCard.vue'
import BuyEthCard from '@/components/MainBodyComponents/BuyEthCard.vue'
import OrderBook from '@/components/MainBodyComponents/OrderBook.vue'
import MarketHistory from '@/components/MainBodyComponents/MarketHistory.vue'
export default {
  components: {
    CurrencyStatsItems,
    EmptyCard,
    BuyEthCard,
    OrderBook,
    MarketHistory
  },
  data () {
    return {
      marketTitles: [
        {
          label: 'DATE',
          prop: 'date'
        },
        {
          label: 'BUY/SELL',
          prop: 'status'
        },
        {
          label: 'BID/ ASK',
          prop: 'buyAsk'
        },
        {
          label: 'TOTAL UNITS(ADA)',
          prop: 'totalUnit'
        },
        {
          label: 'TOTAL COST(BTC)',
          prop: 'totalCost'
        }
      ],
      marketData: [
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'SELL',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        },
        {
          date: '14:55:47',
          status: 'BUY',
          bidAsk: '0.0002132',
          totalUnit: '105.33341177',
          totalCost: '0.00225743'
        }
      ],
      titlesRight: [
        {
          label: 'SUM',
          prop: 'sum'
        },
        {
          label: 'TOTAL',
          prop: 'total'
        },
        {
          label: 'SIZE(ADA)',
          prop: 'size'
        },
        {
          label: 'ASK(BTC)',
          prop: 'ask'
        },
        {
          label: '',
          prop: 'status'
        }
      ],
      tableDataRight: [
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        },
        {
          sum: '0.0000',
          total: '0.0020',
          size: '95.372',
          ask: '0.00002130',
          status: 'BUY'
        }
      ],
      titlesLeft: [
        {
          label: 'SUM',
          prop: 'sum'
        },
        {
          label: 'TOTAL',
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
      tableDataLeft: [
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
      ],
      windowWidth: null,
      ethCards: [
        {
          bitCoins: '0.00000000',
          lowestAsk: '0.05444500',
          price: '0.05450499',
          feeValue: '0.10/0.20%',
          mainHeading: 'BUY ETH',
          secondaryHeading: 'Deposite BTC',
          total: '0'
        },
        {
          bitCoins: '0.00000000',
          lowestAsk: '0.00000000',
          price: '0.05450499',
          feeValue: '0.10/0.20%',
          mainHeading: 'STOP-LIMIT',
          secondaryHeading: "What's this?",
          total: '0'
        },
        {
          bitCoins: '0.00000000',
          lowestAsk: '0.05444500',
          price: '0.05450499',
          feeValue: '0.10/0.20%',
          mainHeading: 'BUY ETH',
          secondaryHeading: 'Deposite BTC',
          total: '0'
        }
      ]
    }
  },
  computed: {
    checkWidth () {
      if (this.windowWidth > 960) {
        return true
      } else {
        return false
      }
    }
  },
  watch: {
    windowWidth: function () {
      this.windowWidth = window.innerWidth
    }
  },
  created () {
    this.windowWidth = window.innerWidth
    this.$nextTick(() => {
      window.addEventListener('resize', () => {
        this.windowWidth = window.innerWidth
      })
    })
  }
}
</script>

<style scoped>
.eth-cards {
  max-width: 410px !important;
}
.eth-cards-special {
  margin-right: 20px
}
.table-card {
  background-color: #424856
}
.table-card-title {
  color: #f1f1f1;
  font-weight: bold;
  font-size: 20px
}
</style>
