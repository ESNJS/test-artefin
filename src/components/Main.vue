<template>
  <v-container>
    <v-row>
      <v-col
        cols="12"
        sm="2"
      >
        <img
          :src="require('../assets/artefin.svg')"
          class="ma-3"
          contain
          height="40"
        />
      </v-col>
      <v-col
        cols="12"
        sm="2"
      >
        <img
          :src="require('../assets/callisto.svg')"
          class="ma-3"
          contain
          height="40"
        />
      </v-col>
      <v-spacer></v-spacer>
      <v-col
        cols="12"
        sm="2"
      >
        <v-btn
          width="220px"
          height="67px"
          outlined
        >
          More About NFT
        </v-btn>
      </v-col>
    </v-row>
    <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <img 
          :src="require('../assets/Cernicky - Fran (hurikan) - Bronze.jpg')"
          width="100%"
        >
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
        <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <img 
          :src="require('../assets/Habl - Cervena kompozice - Bronze.jpg')"
          width="100%"
        >
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
        <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <img 
          :src="require('../assets/Habl - Zlate pohori - Bronze.jpg')"
          width="100%"
        >
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
        <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <img 
          :src="require('../assets/Kintera - Buh - Bronze.jpg')"
          width="100%"
        >
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
        <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <img 
          :src="require('../assets/Kintera - Hlava 1 - Bronze.png')"
          width="100%"
        >
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
        <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <img 
          :src="require('../assets/Kintera - Hlava 2 - Bronze.png')"
          width="100%"
        >
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
        <v-row>
      <v-col
        cols="12"
        sm="6"
      >
        <video width="100%">
          <source :src="require('../assets/Cernicky - Vykrik.mp4')" type="video/mp4">
        Your browser does not support the video tag.
        </video>
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >

      </v-col>
    </v-row>
    <v-row>
      <v-spacer></v-spacer>
      <h1 class="ma-5">Own your arts on the blockchain.</h1> 
      <v-spacer></v-spacer>
    </v-row>
    <v-footer
    class="ma-0"
    dark
    >
      asdas
    </v-footer>
  </v-container>
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

<style>
  .v-btn {
    text-transform: unset !important;
    font-weight: bold;
    font-size: 16px !important; 
    border-width: 3px;
    margin-left: -50  px;
  }
</style>
