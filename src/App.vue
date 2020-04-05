<template>
  <div id="app" class="main-container">
    <h1>The Hooses o' Westeros</h1>
    <houses-list :houses="houses"></houses-list>
    <house-detail :house="selectedHouse"></house-detail>
    <favourite-house :house="favouriteHouse"></favourite-house>
  </div>
</template>

<script>
import HousesList from './components/HouseList.vue'
import HouseDetail from './components/HouseDetail.vue'
import FavouriteHouse from './components/FavouriteHouse.vue'
import { eventBus } from './main.js'

export default {
  name: 'app',
  data(){
    return {
      houses: [],
      selectedHouse: null,
      favouriteHouse: []
    };
  },

  mounted(){
    fetch('https://www.anapioficeandfire.com/api/houses?pageSize=50&hasWords=true')
    .then(result => result.json())
    .then(houses => this.houses = houses)

  eventBus.$on('house-selected', (house) => {
    this.selectedHouse = house
  })

  eventBus.$on('favourite-house', (house) => {
    this.favouriteHouse.push(house)
  })

  },

  components: {
    "houses-list": HousesList,
    "house-detail": HouseDetail,
    "favourite-house": FavouriteHouse
  },

  computed(){
    addHouseToFavourites = function(){
      this.favouriteHouse.push(selectedHouse)
    }
  }

}

</script>

<style scoped>
  .main-container {
    display: flex;
  }

</style>
