<template>
  <div class="prepare-container">
    <input 
      v-model.number="localPlayerCount" 
      type="number" 
      min="1" 
      @change="updatePlayerList" 
      placeholder="How many players?"
    >
    
    <div v-for="(player, index) in players" :key="index" class="player-input">
      <input v-model="player.name" :placeholder="'Player ' + (index + 1) + ' Name'">
    </div>

    <input v-model.number="localScoreMax" type="number" placeholder="Winning score..." />
    <button @click="handleStart">Start Game</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps(['players']);
const emit = defineEmits(['start', 'update:players']);

const localPlayerCount = ref();
const localScoreMax = ref();

const updatePlayerList = () => {
  const currentPlayers = [...props.players];
  if (localPlayerCount.value > currentPlayers.length) {
    for (let i = currentPlayers.length; i < localPlayerCount.value; i++) {
      currentPlayers.push({ name: `Player ${i + 1}`, score: 0 });
    }
  } else {
    currentPlayers.splice(localPlayerCount.value);
  }
  emit('update:players', currentPlayers);
};

const handleStart = () => {
  if (localScoreMax.value <= 0) return alert("Please set a winning score!");
  emit('start', localScoreMax.value);
};
</script>