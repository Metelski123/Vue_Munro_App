<template>
  <div id="app">
    <div id="heading">
      <h1>Munro Bagging</h1>
    </div>

    <div>
      <munros-list :munros="munros"></munros-list>
      <munro-detail :munro="selectedMunro"></munro-detail>
    </div>

    <button class="button" v-if="!favouriteMunro.includes(selectedMunro)" v-on:click="addToFavourite">
    <img src="https://www.psdgraphics.com/wp-content/uploads/2012/04/accept-button.jpg" alt="bottle" width="50" height="50">
    </button>
    <favourite-munro :favouriteMunro="favouriteMunro"></favourite-munro>
  </div>
</template>

<script>

import MunroList from "./components/MunroList.vue";
import MunroDetail from "./components/MunroDetail.vue";
import FavouriteMunro from "./components/FavouriteMunro.vue";

import { eventBus } from './main.js'

export default {
  name: 'app',

  data(){
    return {
    munros: [],
    selectedMunro: null,
    favouriteMunro:[] 
    }
  },
  mounted() {
   fetch('https://munroapi.herokuapp.com/munros')
     .then(res => res.json())
     .then(data => this.munros = data)

   eventBus.$on('selected-munro', (munro) => {
     this.selectedMunro = munro
   })
  },
  methods:{
    addToFavourite: function () {
    if (!this.selectedMunro) return;
    this.favouriteMunro.push(this.selectedMunro)
    }
  },
  components: {
    "munros-list": MunroList,
    "munro-detail": MunroDetail,
    "favourite-munro": FavouriteMunro
  }
}
</script>

<style>
body{
  margin-top: 0;
  margin: 0;
}

#app{
  margin: 0;
  background-image: url(https://d3576n5e2t76p8.cloudfront.net/imager/s3-eu-west-1_amazonaws_com/ws-nts/Production/assets/rte/Kintail-sgurr-a-bhealaich-dheirg-0218_101ea5c78e73b5c692b798d73fdaa9a6.jpg);
  height: 100%;
  width: 100%;
  --text-opacity: 1;
  color: #fff;
}
#heading{

  text-align: center;
}

#option-bar{
  margin: 0 auto;
}

.button{
  margin: 0 auto;
  border: none;
  position: center;
}
</style>