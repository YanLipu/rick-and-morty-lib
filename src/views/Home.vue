<template>
  <div class="home">
    <ListChars/>
  </div>
</template>

<script>
// @ is an alias to /src
import ListChars from '@/components/ListChars.vue'

export default {
  name: 'Home',
  components: {
    ListChars
  }
}
</script>
