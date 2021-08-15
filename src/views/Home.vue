<template>
  <div class="home">
    <Search/>
    <ListChars/>
  </div>
</template>

<script>
// @ is an alias to /src
import Search from '../components/Search.vue'
import ListChars from '@/components/ListChars.vue'

export default {
  name: 'Home',
  components: {
    ListChars,
    Search
  }
}
</script>
