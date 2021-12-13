<template>
  <div>
    <artwork 
      v-for="artwork in lastMintedID-1"
      :key="artwork.id"
      :artwork="artwork"
    />
    <v-footer
      class="ma-0"
      dark
    >
      Artefin
    </v-footer>
  </div>

</template>

<script>
  import Artwork from '../components/Artwork'
  import Artefin from '@/store/contract'
  export default {
    name: 'Home',
    components: {
      Artwork,
    },   
    data: () => ({
      address: "",
      lastMintedID: 0,
    }), 
    beforeMount () {
      web3.eth.requestAccounts().then(addresses => {
        this.address = addresses[0];
      })
      Artefin.methods.last_minted_id().call((err, res) => {
        console.log(res)
        this.lastMintedID = parseInt(res);
      })
    }
  }
</script>
