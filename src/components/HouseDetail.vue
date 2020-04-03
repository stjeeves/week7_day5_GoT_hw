<template>
  <div>
    <h1>{{house.name}}</h1> 
    <p>{{house.region}}</p>
    <p>{{house.coatOfArms}}</p>
    <p>{{house.words}}</p>
   <button v-on:click="handleButton">Choose House</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'house-detail',
    props: ['house'],
    mehthods: {
        handleButton(){
            eventBus.$emit('favourite-house', this.house.name)
        }
    }
}
</script>

<style scoped>

</style>