<template>
  <div class="player-row">
    <p><strong>{{ name }}</strong>: {{ score }}</p>
    <button @click="$emit('addPoint')">+1</button>
  </div>
</template>

<script setup>
defineProps(['name', 'score']);
defineEmits(['addPoint']);
</script>