<template>
  <div id="app">
    <v-header></v-header>
    <div class="tab-wrapper">
      <tab :tabs="tabs" :initialIndex="0"></tab>
    </div>
  </div>
</template>

<script>
import VHeader from './components/v-header/v-header.vue'
import Goods from './components/goods/goods.vue'
import Seller from './components/seller/seller.vue'
import Tab from 'components/tab/tab'

export default {
  name: 'app',
  computed: {
    tabs() {
      return [
        {
          label: '商品',
          component: Goods,
          data: {
            seller: this.seller
          }
        },
        {
          label: '评论',
          component: Seller,
          data: {
            seller: this.seller
          }
        },
        {
          label: '商家',
          component: Seller,
          data: {
            seller: this.seller
          }
        }
      ]
    }
  },
  components: {
    VHeader,
    Tab
  }
}
</script>
<style lang="stylus"></style>
