<template>
  <div id="app">
    <v-header :data="data" @to-show="showCart"></v-header>
    <v-main :data="data" :detail="detail"  @to-show="showCart"></v-main>
    <v-footer></v-footer>
    <v-nav></v-nav>
    <transition name="shop">
      <shopcart :data="data" v-if="show" @to-close="closeCart"></shopcart>
    </transition>
  </div>
</template>

<script>
import header from './components/header/header.vue'
import main from './components/main/main.vue'
import footer from './components/footer/footer.vue'
import nav from './components/nav/nav.vue'
import shopcart from './components/shopcart/shopcart.vue'

const ERR_OK = 0

export default {
  data () {
    return {
      data: {},
      detail: {},
      show: false
    }
  },
  created () {
    if (location.host === 'liaozeen.github.io') {
      let prodPath = 'https://liaozeen.github.io/productDisplay-vue' + '/api/data.json'
      this.$http.get(prodPath).then(response => {
        response = response.body
        this.data = response
        this.detail = response.detail
      })
    } else {
      this.$http.get('/api/phone').then((response) => {
        response = response.body
        if (response.errno === ERR_OK) {
          this.data = response.data
          this.detail = response.data.detail
        }
      })
    }
  },
  methods: {
    showCart () {
      this.show = true
    },
    closeCart () {
      this.show = false
    }
  },
  components: {
    'v-header': header,
    'v-main': main,
    'v-footer': footer,
    'v-nav': nav,
    shopcart
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.shop-enter-active,.shop-leave-active
  transition: all 1s
.shop-enter,.shop-leave-to
  opacity: 0
</style>
