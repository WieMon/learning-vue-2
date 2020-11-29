<template>
<div class='component-container-one'>
  <h3>Game details:</h3>
  <ul>
    <li><span>Game: </span>{{gameName}}</li>
    <li><span>Place: </span>{{gamePlace}}</li>
    <li><span>Number of players: </span>{{gameNumberPlayer}}</li>
  </ul>
  <h3>New players:</h3>
  <div
    class='new-players-list'
    v-for='(player,index) in gameNewPlayers' :key='index'
    @click='removePlayerFromList'>
      {{player}}
  </div>
  <h3>Add new players:</h3>
  <div>
    <input type='text' v-model='addPlayerInput'>
    <button class='btn' @click='addPlayerToList'>Add Player</button>
  </div>
  <div>
    <input type='text' v-model='addGameInput'>
    <button class='btn' @click='addGame'>Add Game</button>
  </div>
</div>
</template>

<script>
  import { bus } from '../main.js';

  export default {
    data() {
      return {
        addPlayerInput: '',
        addGameInput: ''
      }
    },
    props: {
      gameName: String,
      gamePlace: String,
      gameNumberPlayer: Number,
      gameNewPlayersInput: String,
      gameNewPlayers: Array
    },
    methods: {
      addPlayerToList() {
        if(this.validate(this.addPlayerInput)) {
          if(this.gameNewPlayers.length < this.gameNumberPlayer) {
            this.gameNewPlayers.push(this.addPlayerInput);
            this.addPlayerInput='';
          } else {
            alert('Too many players');
            this.addPlayerInput='';
            }
        } else {
          alert('Provide player\'s name');
        }
      },
      removePlayerFromList(index) {
        this.gameNewPlayers.splice(index,1);
      },
      validate(value) {
        if(value !== '') {
          return true;
        } else {
          return false;
        }
      },
      addGame() {
        if(this.validate(this.addGameInput)) {
          bus.$emit('addGame', this.addGameInput);
          this.addGameInput='';
        } else {
            alert('Provide game');
        }

      }
    }
  }
  </script>

<style>
  .component-container-one {
    padding: 0 20px 10px 20px;
    margin: 20px;
    border: 2px solid orange;
    box-shadow: 3px 3px 2px orange;
  }
  .btn {
    margin: 10px 0;
  }
  .new-players-list {
    display: inline-block;
    margin-right: 10px;
    cursor: pointer;
    background: orange;
    color: white;
    padding: 5px 10px;
    border-radius: 5px;
  }
</style>
