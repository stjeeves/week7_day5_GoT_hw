<template>
  <div v-if="house">
      <h1>You have chosen to join:</h1>
      <p v-for="(house, index) in house" :house="house" :key="index">{{house}}></p>
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