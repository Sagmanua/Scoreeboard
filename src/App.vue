<template>
  <div class="container">
    <h1>Scoreboard</h1>

    <PlayerSetup 
      v-if="!gameStarted" 
      v-model:players="players" 
      @start="startGame" 
    />

    <div v-else class="dashboard">
      <ScoreControl 
        v-for="(player, index) in players" 
        :key="index"
        :name="player.name"
        :score="player.score"
        @add-point="addPoint(index)"
      />
      <button class="reset-btn" @click="resetGame">Reset</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import PlayerSetup from './components/PlayerSetup.vue';
import ScoreControl from './components/ScoreControl.vue';

const scoreMax = ref();
const gameStarted = ref(false);
const players = ref([
  { name: 'Player 1', score: 0 },
  { name: 'Player 2', score: 0 }
]);

const startGame = (max) => {
  scoreMax.value = max;
  gameStarted.value = true;
};

const addPoint = (index) => {
  players.value[index].score++;
  
  if (players.value[index].score >= scoreMax.value) {
    alert(`${players.value[index].name} wins!`);
    resetGame();
  }
};

const resetGame = () => {
  gameStarted.value = false;
  players.value.forEach(p => p.score = 0);
};
</script>

