<template>
  <div>
        <div id="title" class="text-center text-white">
            <h1>Rick and Morty Library</h1>
        </div>
        <router-view/>
        
  </div>
</template>

<script>
import Search from './components/Search.vue'
import "bootstrap/dist/css/bootstrap.css"
import "./styles/styles.css"
export default {
  name: 'App',
  components: {
    Search
  }
}
</script>

<style>

</style>
