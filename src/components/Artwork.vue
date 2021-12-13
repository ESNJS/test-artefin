<template>
  <v-container>
    <v-lazy
      v-model="isActive"
      :options="{
      threshold: .5
      }"
      transition="fade-transition"
    >
      <v-img 
          width="50%"
          :src="imagePath"
          :key="artKey"
          @error="errorHandler()"
      ></v-img>
    </v-lazy> 
    <h1>Owner: {{owner}}</h1> 
  </v-container>
</template>

<script>
  import Artefin from '@/store/contract'
  export default {
    props: ['artwork'],
    data: () => ({
      owner: "",
      imagePath: "",
      artKey: 0,
      isActive: false,
      
    }),
    beforeMount () {    
      console.log(parseInt(this.artwork))    
      Artefin.methods.getTokenProperties(parseInt(this.artwork)).call((err, res) => {
        console.log(res.properties[1])
        this.imagePath = res.properties[1]
      })
      Artefin.methods._owners(parseInt(this.artwork)).call((err, res) => {
        console.log(res)
        this.owner = res;
      })
    },    
    methods: {
      errorHandler () {
        this.artKey += 1;
      },
    }
  }
</script>

<style>
  .v-btn {
    text-transform: unset !important;
    font-weight: bold;
    font-size: 16px !important; 
    border-width: 3px;
    margin-left: -50  px;
  }
</style>
