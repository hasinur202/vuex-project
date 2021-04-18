<template>
  <div>
    <nav class="navbar navbar-expand navbar-dark bg-dark">
      <div class="container">
          <ul class="nav navbar-nav">
              <li class="nav-item active">
                  <a class="nav-link" href="#">Home</a>
              </li>
              <li class="nav-item">
                  <a class="nav-link" href="#">Product</a>
              </li>
          </ul>

          <div>
            <div class="dropdown open">
              <button class="btn btn-secondary dropdown-toggle" type="button" id="triggerId" data-toggle="dropdown" aria-haspopup="true"
                  aria-expanded="false">
                    0 Cart
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
import MiniCart from './MiniCart.vue'
export default {
  components: { MiniCart },

}
</script>

<style>

</style>