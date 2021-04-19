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
        ...mapActions('cart', ["removeProductFromCart","clearCartItems","getCartItems"])
    },
    computed: {
        //it will work only when we use namespaced:true
        ...mapState('cart',['cart']),

        // ...mapState({
        //     cart:state => state.cart.cart
        // }),

        ...mapGetters('cart', ['cartTotalPrice'])
    },
    mounted(){
        this.getCartItems();
    }
}
</script>

<style>

</style>