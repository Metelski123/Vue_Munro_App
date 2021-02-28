<template>
  <div>
    <div v-if="!munro">
      <p>Please Select a Munro</p>
    </div>
    <div v-if="munro" class="munros">
      <h3>Name: {{munro.name}}</h3>
      <p> Height: {{munro.abv}}</p>
      <p> Description: {{munro.description}}</p>
      <img class="image" v-bind:src="munro.image_url">
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'munro-detail',
  props: ['munro'],
}
</script>

<style scoped>
.image{
 height: 200px
}

.munros{
  margin: 0 auto;
  width:40%;
}
</style>