<template>
 <div id="option-bar">
   <select id="select" v-on:change='handleSelected' v-model="selectedMunro">
     <option disabled value="">Select munro</option>
     <option v-for="(munro, index) in munros" :value="munro" :key="index">{{munro.name}}</option>
   </select>
 </div>
  
</template>

<script>

import {eventBus} from '../main.js'

export default {
 data(){
   return{
     selectedMunro: {}
   }
 },
 props:['munros'],

 methods: {
  handleSelected() {
    eventBus.$emit('selected-munro', this.selectedMunro)
  }
 }
}
</script>

<style>

#option-bar{
  text-align: center;
}

#select{
  border: 1px gray solid;
  padding: 7px;
  border-radius: 3px;
}

</style>l