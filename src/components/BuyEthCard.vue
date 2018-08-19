<template>
  <v-card class="buy-eth-card">
      <v-container>
        <v-layout row wrap>
          <v-flex md8>
            <p class="main-heading">{{mainHeading}}</p>
            <v-layout row wrap>
              <v-flex md5>
                <p>You have:</p>
              </v-flex>
              <v-flex md6>
                <p>{{bitCoins}} BTC</p>
              </v-flex>
            </v-layout>
            <v-layout row wrap>
              <v-flex md5>
                <p>Lowest Ask:</p>
              </v-flex>
              <v-flex md6>
                <p>{{lowestAsk}} BTC</p>
              </v-flex>
            </v-layout>
          </v-flex>
          <v-flex md4 class="eth-card-right">
            <p class="secondary-heading">{{secondaryHeading}}</p>
          </v-flex>
        </v-layout>
      </v-container>
    <hr>
    <v-layout row>
      <v-container>
        <v-layout row wrap>
          <v-flex md12 class="mb-2">
            <p>Price</p>
            <input type="text" :value="price" class="input-field-text" :class="windowWidth < 1450 ?'input-field' : 'input-field-responsive'">
            <v-btn small depressed disabled flat class="input-btn"><p>BTC</p></v-btn>
          </v-flex>
          <v-flex md12 class="mb-2">
            <p>Amount</p>
            <input type="text" value="" class="input-field-text" :class="windowWidth < 1450 ?'input-field' : 'input-field-responsive'">
            <v-btn small depressed disabled flat class="input-btn"><p>BTC</p></v-btn>
          </v-flex>
          <v-flex md12>
            <p>Total</p>
            <input type="text" value="" class="input-field-text" :class="windowWidth < 1450 ?'input-field' : 'input-field-responsive'">
            <v-btn small depressed disabled flat class="input-btn"><p>BTC</p></v-btn>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex>
            <p>FEE: {{feeValue}}</p>
          </v-flex>
          <v-flex>
            <v-btn class="buy-btn">
              BUY
            </v-btn>
          </v-flex>
        </v-layout>
      </v-container>
    </v-layout>
  </v-card>
</template>
<script>
export default {
  props: ['windowWidth', 'bitCoins', 'lowestAsk', 'price', 'feeValue', 'mainHeading', 'secondaryHeading', 'total'],
  data () {
    return {
    }
  }
}
</script>

<style scoped>
p {
  padding: 0px;
  margin: 0px;
}
.buy-eth-card {
  background-color: #4E5464;
  color: #f1f1f1
}
.eth-card-right p{
  float: right;
}
.main-heading {
  font-size: 30px
}
.secondary-heading {
  color: #A8914E;
  text-decoration: underline;
  cursor: pointer
}
.input-field-text {
  background-color: #4E5464;
  border: 1px solid #f1f1f1;
  border-radius: 4px;
  height: 40px;
  text-align: right;
  z-index: 1;
  position: relative;
  padding-right: 15px;
}
.input-field {
  width: 70%;
}
.input-field-responsive {
  width: 80%;
}
.input-btn {
  background-color: #ACB5C6 !important;
  border-radius: 4px;
  height: 40px;
  margin-top: 3.3px;
  margin-left: -30px;
  z-index: 0;
  box-shadow: none;
  text-align: right;
  color: #f1f1f1 !important
}
.input-btn p {
  color: #f1f1f1 !important;
  margin-left: 20px
}
.buy-btn {
  border-radius: 20px;
  background-color: #D9A30C !important;
  color: #f1f1f1;
  float: right;
}
</style>
