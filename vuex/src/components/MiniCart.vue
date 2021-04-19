<template>
    <div class="dropdown-menu p-2" style="min-width:320px;right:0;left:auto" aria-labelledby="triggerId">
        <div v-for="item in cart" :key="item.product.id">
            <div class="px-2 d-flex justify-content-between">
                <div>
                    <strong>{{ item.product.title }}</strong>
                    <br/>
                    {{ item.quantity }} X ${{ item.product.price }}
                </div>
                <div>
                    <a @click.prevent="removeProductFromCart(item.product)" href="#" class="badge badge-secondary">remove</a>
                </div>
            </div>
            <hr/>
        </div>
        <div class="d-flex justify-content-between">
            <span>Total: ${{ cartTotalPrice }}</span>
            <a @click.prevent="clearCartItems()" href="#">Clear Cart</a>
        </div>
    </div>
</template>

<script>
import { mapState, mapGetters, mapActions } from "vuex";
export default {
    methods:{
        ...mapActions(["removeProductFromCart","clearCartItems","getCartItems"])

        // removeProductFromCart(product){
        //     this.$store.dispatch('removeProductFromCart',product);
        // },

        // clearCartItems(){
        //     this.$store.dispatch('clearCartItems');
        // }
    },
    computed: {
        ...mapState(['cart']),
        ...mapGetters(['cartTotalPrice'])
        // cart(){
        //     return this.$store.state.cart;
        // },

        // cartTotalPrice(){
        //     return this.$store.getters.cartTotalPrice;
        // }
    },
    mounted(){
        this.getCartItems();
        // this.$store.dispatch('getCartItems');
    }
}
</script>

<style>

</style>