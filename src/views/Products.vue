<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <main class="wrapper">
        <div class="card-container">
            <ProductCard
            v-for="(product, index) in inventory"
            :key="product.id"
            class="card"
            :index="index"
            :product="product"
            :addToCart="addToCart"
            />
        </div>
    </main>
</template>

<script>
import ProductCard from '../components/ProductCard.vue'

export default {
  props: ['inventory', 'addToCart'],
  components: {
    ProductCard
  }
}
</script>
