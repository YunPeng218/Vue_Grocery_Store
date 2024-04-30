<template>
  <div class="home">
    <div class="splash-container">
        <div class="splash">
          <h1>Beans Food Market</h1>
        </div>
      </div>

      <main class="wrapper">

        <h2>Recommended</h2>

        <div class="recommended">

          <ProductCard
            v-for="(product, index) in inventory.slice(0, 3)"
            :key="product.id"
            class="card"
            :index="index"
            :product="product"
            :addToCart="addToCart"
          />

        </div>

      </main>
  </div>
</template>

<script>
import ProductCard from '../components/ProductCard.vue'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Home',
  props: ['inventory', 'addToCart'],
  components: {
    ProductCard
  }
}
</script>
