<template>
  <li v-on:click="handleClick">{{house.name}}</li>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'list-item',
    props: ['house'],
    methods: {
        handleClick(){
            eventBus.$emit('house-selected', this.house)
        }
    }
}
</script>

<style scoped>

</style>