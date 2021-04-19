<template>

    <div class="d-flex align-items-lg-stretch flex-wrap">
        <product-card v-for="product in products" :key="product.id" :product="product" />
    </div>
  
</template>

<script>
import { mapState, mapActions } from "vuex";
import ProductCard from './ProductCard.vue'
export default {
  components: { 
    ProductCard 
  },

  computed: {
    ...mapState({
      products: state => state.product.products,
    }),
    // products(){
    //   return this.$store.state.products;
    // }
  },
  methods:{
    ...mapActions(['getProducts']),
  },

  mounted(){
    this.getProducts();
    // this.$store.dispatch('getProducts');
  }

}
</script>

<style>

</style>