<template>
  <div>
        <div id="title" class="text-center text-white">
            <h1>Rick and Morty Library</h1>
        </div>
        <Search/>
        <div>
          <div>

          </div>
          <div>
            
          </div>
        </div>
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
  },
  data: function (){
    return{
      page: 1,
      pageSize: null,
      characters: 'https://rickandmortyapi.com/api/character',
    }
  },
  methods: {
    getCharacterList() {
      const axios = require('axios')
      axios.get(`${ this.characters }/?pages=${ this.page }`).then(response => {
        console.log('response is: ', response.data.results)
        this.pageSize = response.data.results.length
        console.log('o tamanho da pagina é de: ', this.pageSize)
      })
      console.log('Terminou a função')
    }
  },
  created: function() {
    this.getCharacterList()
  } 
}
</script>

<style>

</style>
