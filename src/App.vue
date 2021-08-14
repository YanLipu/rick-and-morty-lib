<template>
  <div>
        <div id="title" class="text-center text-white">
            <h1>Rick and Morty Library</h1>
        </div>
        <Search/>
        <div v-for="chars in charData">
          {{ chars.name }}
          <div>
            <img :src="chars.image" alt="" style="heigth: 50px; width: 50px;">
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
      charData: null,
      characters: 'https://rickandmortyapi.com/api/character',
    }
  },
  methods: {
    getCharacterList() {
      const axios = require('axios')
      axios.get(`${ this.characters }/?page=${ this.page }`).then(response => {
        console.log('response is: ', response.data.results)
        this.pageSize = response.data.results.length
        this.charData = response.data.results
        console.log(this.charData[3].name)        
        console.log('o tamanho da pagina é de: ', this.pageSize)
      })
      console.log('Terminou a função')
    },
    nextPage() {
      if(this.page < 34){
        this.page++
      }
      this.getCharacterList(this.page)
    },
    previousPage() {
      if(this.page > 0){
        this.page--
      }
    }
  },
  created: function() {
    this.getCharacterList()
  } 
}
</script>

<style>

</style>
