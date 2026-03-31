<template>
    <div class="container">
        <h1>Scoreboard</h1>
            <div v-show="prepare" class="prepare-container">
                <input v-model="score_max" type="number" placeholder="Winning score..." />
                <input v-model="player0" placeholder="Name of player 1">
                <input v-model="player1" placeholder="Name of player 2">
                <button @click="start_round">Start Game</button>
            </div>
        
        <div v-show="start" class="dashboard">
                <div class="first">
                    <p>First {{ player0 }} Scoree:{{ value0 }}</p>
                    <button @click="add1">+1</button>
                </div>
                <div class="second">
                    <p>Second {{ player1 }} Scoree:{{ value1 }}</p>
                    <button @click="add2">+1</button>
                </div>

        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue';

const prepare = ref(true);
const start = ref(false);
const score_max = ref(0)

const player0 = ref('Player 1');
const player1 = ref('Player 2');

const value0 = ref(0)
const value1 = ref(0)

const start_round = () => {
    prepare.value = false; 
    start.value = true;
};


const add1 = () =>{
    value0.value++;
    if(value0.value==score_max.value){
        alert("win first player")
    }
}
const add2 = () =>{
    value1.value++;
    if(value0.value==score_max.value){
        alert("win first player")
    }
}

</script>

<style lang="scss">
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

  h1 {
    margin-bottom: 2rem;
  }
}

.dashboard {
    display: flex;
    flex-direction: column;
    gap: 15px; 

    .first, .second {
        display: flex;
        align-items: center;      
        justify-content: space-between; 
        
        padding: 15px 20px;
        background: $primary-bg;
        border: 1px solid $border-color;
        border-radius: 12px;
        transition: transform 0.2s;

        &:hover {
        transform: translateY(-2px);
        border-color: $accent-color;
        }
    }
}
.prepare-container {
    display: flex;
    flex-direction: column;
    gap: 12px;
    padding: 20px;
    background: white;
    border: 1px solid $border-color;
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);

    input {
        padding: 12px 15px;
        border: 1px solid $border-color;
        border-radius: 8px;
        font-size: 1rem;
        outline: none;
        transition: border-color 0.2s;

        &:focus {
            border-color: $accent-color;
        }
    }

    button {
        padding: 12px;
        background-color: $accent-color;
        color: white;
        border: none;
        border-radius: 8px;
        font-weight: bold;
        cursor: pointer;
        font-size: 1rem;
        transition: opacity 0.2s;

        &:hover {
            opacity: 0.9;
        }
        
        &:active {
            transform: scale(0.98);
        }
    }
}
</style>