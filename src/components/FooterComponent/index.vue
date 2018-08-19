<template>
  <div>
    <v-footer class="footer-main" :class="drawer? 'footer' : 'footer-responsive'">
      
      <v-layout row wrap>
        <v-flex md12 sm12 xs12>
          <ul class="nav navbar-right">
            <li v-for="(item, i) in footerListFirst" :key="i" :class="drawer? 'footer-items' : 'footer-items-responsive'">
                <a :href="item.link">
                  <p style="display: inline;">{{item.title}}</p>
                </a>
            </li>
          </ul>
        </v-flex>
        <v-flex md12 sm12 xs12>
          <ul class="nav navbar-right">
            <li v-for="(item, i) in footerListSecond" :key="i" :class="drawer? 'footer-items' : 'footer-items-responsive'">
                <a :href="item.link">
                  <p style="display: inline;">{{item.title}}</p>
                </a>
            </li>
            <li :class="drawer? 'fb' : 'fb-responsive'">
              <a href="#">
                <p style="display: inline;">Follow us on Facebook</p>
              </a>
            </li>
          </ul>
        </v-flex>
        <v-flex :class="drawer? 'footer-heading' : 'footer-heading-responsive'" md12 sm12 xs12>
          <span>2018 EOS Swaps</span>
        </v-flex>
      </v-layout>
    </v-footer>
  </div>
</template>

<script>
export default {
  props: ['drawer'],
  data () {
    return {
      windowWidth: null,
      footerListFirst: [
        {
          title: 'About',
          link: '#'
        },
        {
          title: 'Website Status',
          link: '#'
        },
        {
          title: 'Cookies',
          link: '#'
        },
        {
          title: 'Fees',
          link: '#'
        },
        {
          title: 'Support',
          link: '#'
        },
        {
          title: 'Follow us on Twitter',
          link: '#'
        }
      ],
      footerListSecond: [
        {
          title: 'Privacy',
          link: '#'
        },
        {
          title: 'API Documents',
          link: '#'
        },
        {
          title: 'Terms',
          link: '#'
        },
        {
          title: 'Contact',
          link: '#'
        }
      ]
    }
  }
}
</script>


<style scoped>
.footer-main {
  height: 100px !important;
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
.nav {
  list-style: none;
  margin: 0;
  padding: 0;
}
ul {
  display: inline-flex;
}
.nav > li > a {
  text-decoration: none;
  color: #747A8A;
  padding-bottom: 10px;
}
.nav > li > a:hover, a:focus {
  font-weight: bold;
  color: #F1F1F1;
}
.fb {
  width: 400px;
  float: right;
  padding-left: 243px;
}
.fb-responsive {
  width: 480px;
  float: right;
  padding-left: 303px;
}
.footer-heading {
  padding-top: 10px;
  margin-left: -30px;
  text-align: center
}
.footer-heading-responsive {
  padding-top: 10px;
  margin-left: -30px;
  text-align: center
}
.footer-items {
  width: 200px;
  text-align: center;
  padding-left: 12px;
}
.footer-items-responsive {
  width: 240px;
  text-align: center;
  padding-left: 12px;
}
</style>
