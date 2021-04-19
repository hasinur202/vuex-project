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
            <a href="#">Clear Cart</a>
        </div>
    </div>
</template>

<script>
export default {
    methods:{
        removeProductFromCart(product){
            this.$store.dispatch('removeProductFromCart',product);
        }
    },
    computed: {
        cart(){
            return this.$store.state.cart;
        },

        cartTotalPrice(){
            return this.$store.getters.cartTotalPrice;
        }
    },
    mounted(){
        this.$store.dispatch('getCartItems');
    }
}
</script>

<style>

</style>