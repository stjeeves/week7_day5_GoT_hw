<template>
  <div id="app" class="main-container">
    <h1>The Hooses o' Westeros</h1>
    <houses-list :houses="houses" class="houses-list"></houses-list>
    <house-detail :house="selectedHouse" class="selected-house"></house-detail>
    <favourite-house :house="favouriteHouse" class="favourite-house"></favourite-house>
    <!-- <img src="https://i2-prod.birminghammail.co.uk/incoming/article16042205.ece/ALTERNATES/s615b/0_Iron-Throne.jpg" alt="The Iron Throne"> -->
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
    align-items: flex-start;
    flex-direction: column;
    justify-content: space-between;
    /* background-color: gray;  */
    /* background-image: url(https://i2-prod.birminghammail.co.uk/incoming/article16042205.ece/ALTERNATES/s615b/0_Iron-Throne.jpg);
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;  */
    font-family: 'Playfair Display SC', serif;
    
  }

  .main-container::after {
  content: "";
  background: url(https://i2-prod.birminghammail.co.uk/incoming/article16042205.ece/ALTERNATES/s615b/0_Iron-Throne.jpg);
  opacity: 0.5;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position:fixed;
  z-index: -1; 
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;  
  }


  .houses-list{
    order: 2;
    color: black;
  }

  .selected-house{
    order: 1;
    color: black;
  }

  .favourite-house{
    order: 3;
    color: black;
  }

  h1{
    width: 100%;
    color: black;
  }

  /* img{
    height:100%;
    width: 100%;
    opacity: 0.4;
  } */

</style>
