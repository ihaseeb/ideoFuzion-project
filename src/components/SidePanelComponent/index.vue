<template>
  <v-navigation-drawer
    persistent
    v-model="drawer"
    enable-resize-watcher
    fixed
    app
    class="side-panel"
  >
    <v-list>

      <v-list-tile class="main-heading-panel">
        <v-list-tile-content>
          <v-list-tile-title>
            <p class="main-heading sp-values"><v-icon>bubble_chart</v-icon><B>EOS</B> SWAPS</p>
          </v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>

      <v-list-tile class="">
        <v-list-tile-content>
          <v-list-tile-title>
            <p class="markets">MARKETS</p>
            <v-icon class="markets-icon" @click.stop="closeSidePanelClicked" dark size='large'>chevron_leftt</v-icon>
          </v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
      
      <v-list-tile class="mini-nav-bar">
        <v-list-tile-content>
          <ul class="nav navbar-right">
            <li v-for="(item, i) in miniNavList" :key="i">
                <a href="#">
                  <p style="display: inline;">{{item}}</p>
                </a>
            </li>
          </ul>
        </v-list-tile-content>
      </v-list-tile>

      
      <v-list-tile class="search-field">
        <v-list-tile-content>
          <input type="text" value="" placeholder="Search" class="input-field-text">
        </v-list-tile-content>
      </v-list-tile>

      <v-list-tile
        value="true"
        v-for="(item, i) in sidePanelStats"
        :key="i"
        class="list-tile"
      >
        <a style="width: 100%;" href="#" class="sp-links">
        <v-list-tile-content>
          <v-list-tile-title class="list-items">
            <v-layout row wrap>
              <v-flex md6 sm6 xs6 class="sp-list-left">
                <p class="sp-values">{{item.title}}</p>
                <p class="sp-stats sp-bottom sp-values">{{item.currentValue}}</p>
              </v-flex>
              <v-flex md6 sm6 xs6>
                <p class="sp-stats sp-right" :class="item.changedValuePercentage < 0 ? 'arrow-downward' : 'arrow-upward'">{{item.changedValuePercentage}}%
                  <v-icon v-if="Number(item.changedValuePercentage) < 0" class="arrow-icon arrow-downward">arrow_downward</v-icon>
                  <v-icon v-if="Number(item.changedValuePercentage) > 0" class="arrow-icon arrow-upward">arrow_upward</v-icon>
                </p>
                <p class="sp-stats sp-bottom sp-right sp-values">{{item.changedValue}}</p>
              </v-flex>
            </v-layout>
          </v-list-tile-title>
        </v-list-tile-content>
        </a>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  props: ['drawer'],
  created () {
    this.drawerValue = this.drawer
  },
  data () {
    return {
      drawerValue: true,
      clipped: false,
      fixed: false,
      sidePanelStats: [
        {
          title: 'USDT',
          currentValue: '41062.10',
          changedValue: '0.99800000',
          changedValuePercentage: '-0.1'
        },
        {
          title: 'TUSD',
          currentValue: '0.00',
          changedValue: '0.99800000',
          changedValuePercentage: '0.0'
        },
        {
          title: 'ETH',
          currentValue: '144401.44',
          changedValue: '482.00000000',
          changedValuePercentage: '3.0'
        },
        {
          title: 'ETH',
          currentValue: '241833.32',
          changedValue: '6750.77000000',
          changedValuePercentage: '2.4'
        }
      ],
      miniNavList: ['USD', 'BTC', 'ETH', 'USDT']
    }
  },
  methods: {
    closeSidePanelClicked () {
      this.drawerValue = !this.drawer
      this.$emit('drawerChanged', this.drawerValue)
    }
  }
}
</script>

<style scoped>
.main-heading {
  font-size: 20px;
}
.main-heading-panel {
  border-bottom-color: #5F6573;
  border-bottom-width: thin ;
  border-bottom-style: inset;
  height: 57px;
  margin-bottom: 15px;
}
.list-tile {
  height: 75px !important;
  z-index: 1;
}
.side-panel {
  width: 200px !important;
  background-color: #464C5A;
  border-right-color: #5F6573;
  border-right-width: thin;
  border-right-style: inset;
  max-height: 100%!important;
}
.markets {
  display: inline;
  color: #f1f1f1;
  font-size: 18px;
}
.markets-icon {
  float: right;
  margin-top: 2px;
  margin-right: -15px
}
.sp-links {
  text-decoration: none !important;
  margin-top: 45px;
}
.list-tile:hover, .list-tile:focus {
  background-color: rgb(98, 107, 133);
  border-left-color: darkorange;
  border-left-width: 2px ;
  border-left-style: inset;
}
.list-items {
  height: 70px !important;
}
.arrow-icon {
  font-size: 14px
}
.arrow-upward {
  color:springgreen
}
.arrow-downward {
  color:darkorange
}
.sp-stats {
  font-size: 12px;
}
.sp-bottom {
  margin-top: -15px
}
.sp-right {
  float: right;
}
.sp-values {
  color: #F1F1F1;
}
.sp-list-left{
  z-index: 1000;
}

.nav {
  list-style: none;
  margin: 0;
  padding: 0;
  margin-left: -15px;
  margin-bottom: -10px;
}
ul {
  display: inline-flex;
}
li {
  width: 44px;
  text-align: center;
  padding-left: 12px;
}
.nav > li > a {
  text-decoration: none;
  color: #747A8A;
  padding-bottom: 10px;
}
.nav > li > a:hover, a:focus {
  font-weight: bold;
  color: #F1F1F1;
  border-bottom-color: darkorange;
  border-bottom-width: 2px ;
  border-bottom-style: inset;
  z-index: 2;
  position: relative;
}
.mini-nav-bar {
  /* margin-bottom:-5px; */
  border-bottom-color: #5F6573;
  border-bottom-width: thin ;
  border-bottom-style: inset;
  z-index: 1;
}
.search-field {
  /* height: 40p; */
  color: #8B90A3
}
.input-field-text {
  background-color: #8B90A3;
  height: 30px;
  z-index: 1;
  padding-left: 10px;
  color: #f1f1f1
}
</style>
