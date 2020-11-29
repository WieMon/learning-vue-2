<template>
  <div class='component-container-two'>
    <h3>Games: </h3>
    <ul>
      <li v-for='(game,index) in games' :key='index'>
        {{game}}
      </li>
    </ul>
  </div>
</template>

<script>
  import { bus } from '../main.js';

  export default {
    data() {
      return {
        games: []
      }
    },
    created() {
      bus.$on('addGame',(value)=>{
        this.games.push(value)
      })
    }
  }
</script>

<style>
  .component-container-two {
    padding: 0 20px 10px 20px;
    margin: 20px;
    border: 2px solid purple;
    box-shadow: 3px 3px 2px purple;
  }
</style>
