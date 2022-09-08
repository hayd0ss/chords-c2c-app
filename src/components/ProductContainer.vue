<template>
  <div class="product-div">
    <div class="product-container">
      <ProductCard
        v-for="vinyl in records"
        :key="vinyl.id"
        :vinyls="vinyl"
      />
    </div>
  </div>
</template>

<script>
import ProductCard from '../components/ProductCard.vue'
import ProductService from '../services/ProductService.js'
// const api = 'https://vc-products.netlify.app/.netlify/functions/api/'

export default {
  name: 'ProductContainer',
  // props: { vinyls: Object },
  methods: {},
  data() {
    return {
      records: null,
    }
  },
  components: {
    ProductCard,
  },
  created() {
    ProductService.getDatas()
      .then(response => {
        // console.log(response.data);
        this.records = response.data
      })
      .catch(error => {
        console.log(error)
      })
  },
}
</script>
<style lang="scss" scoped>
.product-div {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.product-container {
  display: grid;
  grid-template-columns: auto auto auto;
}

@media only screen and (max-width: 1200px) {
  .product-container {
    grid-template-columns: auto auto;
    column-gap: 3rem;
  }
}

@media only screen and (min-width: 1500px) {
  .product-container {
    grid-template-columns: auto auto auto auto;
    column-gap: 2rem;
  }
}
</style>
