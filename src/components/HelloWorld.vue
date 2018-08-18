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
      <v-flex md4 class="eth-cards" v-for="(card, i) in ethCards" :key="i" :class="i !== 2 && checkWidth ? 'eth-cards-special' : 'eth-cards-special-responsive'">
        <buy-eth-card
          :bitCoins='card.bitCoins'
          :lowestAsk='card.lowestAsk'
          :price='card.price'
          :feeValue='card.feeValue'
          :mainHeading='card.mainHeading'
          :secondaryHeading='card.secondaryHeading'
          :total='card.total'></buy-eth-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import CurrencyStatsItems from './CurrencyStatComponent'
import EmptyCard from './emptyCard'
import BuyEthCard from './BuyEthCard'
export default {
  components: {
    CurrencyStatsItems,
    EmptyCard,
    BuyEthCard
  },
  data () {
    return {
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
  min-width: 240px !important;
  max-width: 410px !important;
}
.eth-cards-special {
  margin-right: 20px
}
</style>
