<template>
  <div v-if="house">
      <h1>You have chosen to join:</h1>
      <h2 v-for="(house, index) in house" :house="house" :key="index">{{house}}</h2>
      <p>Remember, in the game of thrones, you win or you die.</p>
  </div>
</template>

<script>
import HouseDetail from './HouseDetail.vue'

export default {
    name: 'favourite-house',
    props: ['house'],
    components:{
        "house-detail" :HouseDetail
    }
}
</script>

<style scoped>

</style>