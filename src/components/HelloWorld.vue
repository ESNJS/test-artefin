<template>
  <div>
        <v-img
          :src="require('../assets/logo.png')"
          class="my-3"
          contain
          height="150"
        />
        <v-card
          align="center"
          flat
          color="grey"
          class="pa-5"
        >
          <v-img 
            :src="tokenImage"
            height="400px"
            width="250px"
          ></v-img>
          <v-card-title>{{tokenArtist}}</v-card-title>
       </v-card>
  </div>
</template>

<script>
  import Artefin from '@/store/contract'
  export default {
    data: () => ({
      tokenImage: '',
      tokenArtist: '',
    }),
    beforeMount () {
      Artefin.methods.getTokenProperties(0).call((err, res) => {
        console.log(res)
        this.tokenImage = res.properties[0]
        this.tokenArtist = res.properties[1]
      })
    }
  }
</script>
