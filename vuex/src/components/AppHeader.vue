<template>
  <div>
    <nav class="navbar navbar-expand navbar-dark bg-dark">
      <div class="container">
          <ul class="nav navbar-nav">
              <li class="nav-item active">
                  <router-link to="/" class="nav-link active">Home</router-link>
              </li>
              <li class="nav-item">
                  <router-link to="/product" class="nav-link">Product</router-link>
              </li>
          </ul>

          <div>
            <div class="dropdown open">
              <button class="btn btn-secondary dropdown-toggle" type="button" id="triggerId" data-toggle="dropdown" aria-haspopup="true"
                  aria-expanded="false">
                    {{ cartItemCount }} Cart
                  </button>

                  <div @click="$event.stopPropagation()">
                    <mini-cart/>
                  </div>
              
            </div>
          </div>
      
      </div>

    </nav>

  </div>
</template>

<script>
import { mapGetters } from "vuex";
import MiniCart from './MiniCart.vue'
export default {
  components: { MiniCart },

//way-1
  // computed:{
  //   cartItemCount(){
  //     return this.$store.getters.cartItemCount;
  //   }
  // }

//way-2
  // computed: mapGetters({
  //     cartCount: "cartItemCount"
  // })

//way-3
  // computed: mapGetters(["cartItemCount"])

  //way-4
  computed: {
    //we can use here other computed properties
    ...mapGetters('cart', ["cartItemCount"])
  }

}
</script>

<style>

</style>