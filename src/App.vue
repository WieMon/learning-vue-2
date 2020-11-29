<template>
<div>
 <ComponentOne
  :gameName='name'
  :gamePlace='place'
  :gameNumberPlayer='numberPlayers'
  :gameNewPlayersInput='newPlayersInput'
  :gameNewPlayers='newPlayers'
  @addPlayer='newPlayersInput=$event'
  />
  <!-- <ComponentTwo>

  </ComponentTwo> -->
</div>
</template>

<script>
import ComponentOne from './Components/ComponentOne.vue';
// import ComponentTwo from './Components/ComponentTwo.vue';


export default {
  data() {
    return {
      name: 'Game of Thrones',
      place: 'The North',
      numberPlayers: 8,
      newPlayersInput:'',
      newPlayers: []
    }
  },
  components: {
    ComponentOne
  }
}
</script>

<style>
</style>
