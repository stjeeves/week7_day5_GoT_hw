<template>
  <div>
      <h1>Houses</h1>
      <ul>
          <list-item v-for="(house, index) in houses" :house="house" :key="index"></list-item>
      </ul>
  </div>
</template>

<script>
import ListItem from './HouseListItem.vue';

export default {
    name: 'houses-list',
    props: ['houses'],
    components: {
        "list-item": ListItem
    }
}
</script>

<style scoped>

</style>