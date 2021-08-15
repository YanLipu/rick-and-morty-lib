<template>
    <div id="buscas" class="col-sm text-center">
          <div class="container">
            <div class="row">
              <div class="col-sm">
                <div class="text-white">
                  <h3>Buscar por personagem</h3>
                  <input class="entrada col-12" v-model="searchChar" @keyup.enter="getCharacterData" placeholder="Search character">
                </div>
               </div>
                <div class="col-sm">
                  <div class="text-white">                
                    <h3>Buscar por episódio</h3>
                    <input class="entrada col-12" v-model="searchEp" @keyup.enter="getEpisodesData" placeholder="Search episode" type="text" >
                 </div>
                </div>
            </div>  
          </div>
          <Results :chars="{charData}" v-if="showResults"/>
    </div>
</template>
<script>
import Results from './Results.vue'
export default {
  name: 'Search',
  components: {
    Results
  },
  data: function (){
    return{
      searchChar: '',
      searchEp: '',
      charData: null,
      epData: null,
      showResults: false,
      apiUrl: 'https://rickandmortyapi.com/api',
      characters: 'https://rickandmortyapi.com/api/character',
      locations: 'https://rickandmortyapi.com/api/location',
      episodes: 'https://rickandmortyapi.com/api/episode'
    }
  },
  methods: {
    getCharacterLog() {
      console.log('getCharacter')
    },
    getCharacterData() {
      // console.log('getCharacterData')
      // this.$axios(`${ this.characters }?name=${ this.searchChar }`).then(response => {
      //   console.log('response: ', response.data)
      //   this.charData = response.data
      // })
      const axios = require('axios')
      axios.get(`${ this.characters }/?name=${ this.searchChar }`).then(response => {
        console.log('response is: ', response.data.results)
        this.charData = response.data
      })
      this.showResults = true
      // this.$emit(this.charData)
      // this.$router.push('/results')
      console.log('Terminou a função')
    },
    getEpisodesData() {
      const axios = require('axios')
      axios.get(`${ this.episodes }/?episode=${ this.searchEp }`).then(response => {
        console.log('response is:', response.data.results)
        this.epData = response.data
      })
      this.showResults = true
      // this.$router.push('/results')
      console.log('Terminou a função')
    }
  }
  
}
</script>