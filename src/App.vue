<template>
  <div>
        <div id="title" class="text-center">
            <h1>Rick and Morty Library</h1>
        </div>
        <Search/>
        <div id="main" class="main">
          <div class="container max-height-1000">
            <div class="row content-center">
              <div class="col-md-6 card-infos " id="card-character" v-for="character in characters" v-bind:key="character">
                      <div>
                        <label for=""></label>
                      </div>
                      <div>
                        <img src="https://rickandmortyapi.com/api/character/avatar/1.jpeg" alt="" style="width: 100px; height: 100px; border-radius: 8px;">

                      </div>
                </div>
            </div>
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

  created: function(){
    axios.get('https://rickandmortyapi.com/api/character/').then(response => (console.log(response.data)));
    
  },
  data: function (){
    return{
      characters: [],
    }
  }
  // methods:{
  //   listCharacters(id){
  //     this.characterId = id;
  //     console.log(this.characterId)
  //     axios.get(`https://rickandmortyapi.com/api/character/${this.characterId}`)
  //   }
  // }
}
</script>

<style>

</style>
