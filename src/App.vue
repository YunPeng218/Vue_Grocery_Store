<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
    </nav>
    <div @click="toggleSideBar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ numOfCartItem }})</span>
    </div>
  </header>
  <router-view :inventory="inventory" :addToCart="addToCart" />

  <Sidebar
    v-if="showSideBar"
    :toggle="toggleSideBar"
    :cart="cart"
    :inventory="inventory"
    :remove="removeItem"
  />
</template>

<script>
import Sidebar from './components/Sidebar.vue'
import food from './food.json'

export default {
  components: {
    Sidebar
  },
  data () {
    return {
      showSideBar: false,
      inventory: food,
      cart: {},
      numOfCartItem: 0
    }
  },
  methods: {
    addToCart (name, quantity) {
      if (!Number.isNaN(quantity) && quantity > 0) {
        if (!this.cart[name]) this.cart[name] = 0
        this.cart[name] += quantity
        this.numOfCartItem = Object.keys(this.cart).length
      }
    },
    toggleSideBar () {
      this.showSideBar = !this.showSideBar
    },
    removeItem (name) {
      delete this.cart[name]
      this.numOfCartItem = Object.keys(this.cart).length
    }
  }
}
</script>
