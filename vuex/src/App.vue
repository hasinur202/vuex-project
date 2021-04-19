<template>
  <div id="app">
      <app-header/>
      <div class="container">
        <router-view></router-view>
      </div>
      
      <notifications-list/>

  </div>
</template>

<script>

import AppHeader from './components/AppHeader.vue'
import NotificationsList from './components/NotificationsList.vue'


export default {
  name: 'App',
  components: {
    AppHeader,
    NotificationsList
    
  }
}
</script>

