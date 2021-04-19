<template>
  <div class="row mt-5" v-if="product">
      <div class="col-4">
          <img :src="product.image" class="w-100" alt="">
      </div>
      <div class="col-8">
          <h1>{{ product.title }}</h1>
          <h3>${{ product.price }}</h3>

          <input type="number" v-model.number="quantity" class="text-center col-1 mr-2 p-1"/>
          <button @click="addToCart" class="btn btn-primary">Add to Cart</button>

          <p class="mt-4">{{ product.description }}</p>
      </div>
  </div>
</template>

<script>
import { mapState, mapActions } from "vuex";
export default {
    props: ['id'],

    data(){
        return {
            quantity:1
        }
    },

    methods:{
        ...mapActions(["addProductToCart", "getProduct"]),
        addToCart(){
            this.addProductToCart({
                product: this.product,
                quantity:this.quantity
            });
            // this.$store.dispatch('addProductToCart', {
            //     product: this.product,
            //     quantity:1
            // });
        }
    },

    computed:{
        ...mapState(['product']),
        // product(){
        //     return this.$store.state.product;
        // }
    },

    mounted(){
        this.getProduct(this.id);
        // this.$store.dispatch('getProduct', this.id);
    }
}
</script>

<style>

</style>