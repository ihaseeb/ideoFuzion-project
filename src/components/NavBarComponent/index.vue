<template>
  <div>
    <v-toolbar
      :class="drawer ? 'navbar' : ''"
      app
      class="navbar-nav">
      <v-toolbar-side-icon dark @click.stop="openSidePanelClicked" v-if="drawer === false"></v-toolbar-side-icon>
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
  </div>
</template>

<script>
export default {
  props: ['drawer'],
  data () {
    return {
      clipped: false,
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
      socketStatus: 'Connected'

    }
  },
  methods: {
    openSidePanelClicked () {
      this.drawerValue = !this.drawer
      this.$emit('drawerChanged', this.drawerValue)
    }
  }
}
</script>
<style scoped>

.navbar {
  padding-left: 200px !important;
}
.navbar-nav {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
  /* box-shadow: none; */
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
.arrow-upward {
  color:springgreen
}
.arrow-downward {
  color:darkorange
}
</style>
