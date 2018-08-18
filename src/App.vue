<template>
  <v-app>
    <v-navigation-drawer
      persistent
      :mini-variant="miniVariant"
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
    <v-toolbar
      :class="drawer ? 'navbar' : ''"
      app
      class="navbar-nav">
      <v-toolbar-side-icon @click.stop="drawer = !drawer" v-if="drawer === false"></v-toolbar-side-icon>

      <v-toolbar-title class="socket-status">
        <v-icon v-if="socketStatus === 'Connected'" class="arrow-upward" size="medium">wifi</v-icon>
        <v-icon v-if="socketStatus === 'Not Connected'" class="arrow-downward" size="medium">wifi_off</v-icon>
          Socket Status = {{socketStatus}}
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <ul class="nav navbar-right">
        <li v-for="(item, i) in navItemsList" :key="i">
            <a :href="item.link">
              <p style="display: inline;">{{item.title}}</p>
            </a>
        </li>
        <li class="navSettingList">
            <a class="navSettingLink">
              <v-icon dark size="medium">settings</v-icon>
            </a>
        </li>
      </ul>
    </v-toolbar>
    <div :class="drawer? 'navbar-bottom' : 'navbar-bottom-responsive'"><hr></div>
    <v-content :class="drawer? 'main-container' : 'main-container-responsive'">
      <router-view/>
    </v-content>
    <v-footer :fixed="fixed" app :class="drawer? 'footer' : 'footer-responsive'">
      <span>&copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      navItemsList: [
        {
          title: 'Markets',
          link: '#'
        },
        {
          title: 'Orders',
          link: '#'
        },
        {
          title: 'Wallets',
          link: '#'
        },
        {
          title: 'Settings',
          link: '#'
        },
        {
          title: 'Logout',
          link: '#'
        }
      ],
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
      miniVariant: false,
      right: true,
      rightDrawer: false,
      socketStatus: 'Connected'

    }
  },
  name: 'App'
}
</script>
<style scoped>
.main-container {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
  padding-left: 200px !important;
  padding-top: 0px !important;
}
.main-container-responsive {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
}
hr {
  background-color: #F1F1F1
}
.navbar {
  padding-left: 200px !important;
}
.navbar-nav {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
  box-shadow: none;
}
.navbar-bottom {
  padding-top: 64px;
  padding-left: 225px;
  padding-right: 25px;
  background-image: linear-gradient(90deg, #444A58, #2F353F);
}
.navbar-bottom-responsive {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
}
.main-heading {
  font-size: 20px;
}
.main-heading-panel {
  border-bottom-color: white;
  border-bottom-width: thin ;
  border-bottom-style: inset;
  height: 57px;
  margin-bottom: 15px;
}
.nav {
  list-style: none;
  margin: 0;
  padding: 0;
}
.socket-status {
  font-size: 12px;
  color: #F1F1F1
}
ul {
  display: inline-flex;
}
li {
  width: 80px;
  text-align: center
}
.nav > li > a {
  text-decoration: none;
  color: #F1F1F1;
}
.nav > li > a:hover, a:focus {
  background-color: transparent;
  color: #A8914E
}
.navSettingList {
  width: 20px !important;
}
.list-tile {
  height: 75px !important;
  z-index: 1;
}
.side-panel {
  width: 200px !important;
  background-color: #464C5A;
  border-right-color: white;
  border-right-width: thin;
  border-right-style: inset;
  max-height: 100%!important;
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
.footer {
  background-color: #3E4454;
  color: white;
  margin-left: 200px;
  padding-left: 10px;
}
.footer-responsive {
  background-color: #3E4454;
  color: white;
  padding-left: 10px;
}
</style>
