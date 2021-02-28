<template lang="html">
  <div id="favourite">
    <h2>Favourite Munros</h2>
      <p v-for="(favouriteMunro, index) in favouriteMunro" :key="index">{{favouriteMunro.name}} <img class="small" :src="favouriteMunro.image_url"></p>
      <button v-on:click="removeMunro">
        <img src="https://www.psdgraphics.com/wp-content/uploads/2012/04/delete-button.jpg" alt="bottle" width="50" height="50">
      </button>
  </div>
</template>

<script>
import MunroListVue from './MunroList.vue'
export default {
  name: 'favourite-munro',
  props: ['favouriteMunro'],

  methods:{
    removeMunro: function(index) {
      return this.favouriteMunro.splice(index, 1)
    }
  }
}
</script>

<style lang="css" scoped>

  #favourite{
    padding: 30px;
    text-align: center;
}

.small{
  height: 100px;
}

</style>