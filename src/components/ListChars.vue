<template>
  <div class="main-content">
          <div class="card card-infos" v-for="chars in charData">
            <div class="card-body">
              <div class="card-data">
                <h4>{{ chars.name }}</h4>
                <p>{{ chars.location.name }}</p>
              </div>
              <div class="card-image">
                <img :src="chars.image" class="img-style">
              </div>
            </div>            
            <div class="card-actions">
              <button class="button-info" @click="showInformation()">
                More Informations
              </button>
            </div>
            <Character v-show="isModalVisible" @close="closeModal()"/>
          </div>
          <div class="pages-control">
            <div class="buttons">
              <button class="button-control" @click="previousPage()">Previous</button>
              <button class="button-control" @click="nextPage()">Next</button>
            </div>
          </div>
        </div>
</template>

<script>
import Character from './Character.vue'
export default {
  name: 'ListChars',
  components: {
    Character
  },
  data: function (){
    return{
      page: 1,
      pageSize: null,
      charData: null,
      characters: 'https://rickandmortyapi.com/api/character',
      isModalVisible: false
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
      
      console.log('esta clicando')
      if(this.page < 34){
        this.page++
      }
      this.getCharacterList(this.page)
    },
    previousPage() {
      if(this.page > 1){
        this.page--
      }
      this.getCharacterList(this.page)
    },
    showInformation() {
      console.log('função de abrir modal')
      this.isModalVisible = true
    },
    closeInformation() {
      this.isModalVisible = false
    }
  },
  created: function() {
    this.getCharacterList()
  }
}
</script>

<style>

</style>