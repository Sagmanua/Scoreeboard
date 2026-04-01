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

<style lang="scss">
/* Keep your existing SCSS here */
</style><style lang="scss">
$primary-bg: #f8f9fa;
$border-color: #e0e0e0;
$text-color: #2c3e50;
$accent-color: #42b883;

.container {
  max-width: 500px;
  margin: 40px auto;
  text-align: center;
  font-family: sans-serif;
  color: $text-color;
}

.prepare-container, .player-row {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 20px;
  background: white;
  border: 1px solid $border-color;
  border-radius: 12px;
  margin-bottom: 10px;

  input {
    padding: 10px;
    border-radius: 8px;
    border: 1px solid $border-color;
  }
}

.player-row {
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

button {
  padding: 10px 20px;
  background-color: $accent-color;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;

  &:hover { opacity: 0.8; }
}

.reset-btn {
  background-color: #e74c3c;
  margin-top: 20px;
}
</style>