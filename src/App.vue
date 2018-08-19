<template>
  <v-app>
    <!-- Side panel component -->
    <side-panel-component @drawerChanged='getDrawerValue($event)' :drawer='drawer'></side-panel-component>
    <!-- Nav bar component -->
    <nav-bar-component @drawerChanged='getDrawerValue($event)' :drawer='drawer'></nav-bar-component>
    <div :class="drawer? 'navbar-bottom' : 'navbar-bottom-responsive'">
      <!-- <hr> -->
    </div>
    <v-content :class="drawer? 'main-container' : 'main-container-responsive'">
      <router-view/>
    </v-content>
    <!-- footer component -->
    <footer-component :drawer='drawer'></footer-component>
  </v-app>
</template>

<script>
import SidePanelComponent from '@/components/SidePanelComponent/index.vue'
import NavBarComponent from '@/components/NavBarComponent/index.vue'
import FooterComponent from '@/components/FooterComponent/index.vue'
export default {
  components: {
    SidePanelComponent,
    NavBarComponent,
    FooterComponent
  },
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      miniVariant: false
    }
  },
  methods: {
    getDrawerValue (data) {
      this.drawer = data
    }
  },
  name: 'App'
}
</script>
<style scoped>
/* Main container CSS */

.main-container {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
  padding-left: 200px !important;
  padding-top: 0px !important;
  padding-bottom: 100px !important;
}
.main-container-responsive {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
}
hr {
  background-color: #F1F1F1
}

/* NavBar CSS */

.navbar-bottom {
  padding-top: 64px;
  padding-left: 225px;
  padding-right: 25px;
  background-image: linear-gradient(90deg, #444A58, #2F353F);
}
.navbar-bottom-responsive {
  background-image: linear-gradient(90deg, #444A58, #2F353F);
}
</style>
