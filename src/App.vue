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
  <ComponentTwo />
  <ComponentThree>
    <ul slot='weapons-for-game'>
      <li v-for='(weapon,index) in weapons' :key='index'>
        {{weapon}}
      </li>
    </ul>
  </ComponentThree>

</div>
</template>

<script>
import ComponentOne from './Components/ComponentOne.vue';
import ComponentTwo from './Components/ComponentTwo.vue';
import ComponentThree from './Components/ComponentThree.vue';

export default {
  data() {
    return {
      name: 'Game of Thrones',
      place: 'The North',
      numberPlayers: 8,
      newPlayersInput:'',
      newPlayers: [],
      weapons: ['sword', 'bow', 'knife']
    }
  },
  components: {
    ComponentOne,
    ComponentTwo,
    ComponentThree
  }
}
</script>

<style>
</style>
