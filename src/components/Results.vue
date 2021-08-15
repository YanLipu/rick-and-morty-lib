<template>
  <div class="main-content">
          <!-- <div class="card card-infos" v-for="chars in charData"> -->
            <div class="card-body">
              <div class="card-data">
                <h4>{{ charData.name }}</h4>
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
          <!-- </div> -->
          <div class="pages-control">
            <div class="buttons">
              <button class="button-control" @click="previousPage()">Previous</button>
              <button class="button-control" @click="nextPage()">Next</button>
            </div>
          </div>
        </div>
</template>

<script>
export default {
  name: 'Result',
  props: {
    chars:{
      required: true,
      type:Object
    }
  }
}
</script>

<style>

</style>