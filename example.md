<template>
<div class="container">
    <button @click="menos">-</button>
    <span>{{ dia }}</span>
    <button @click="plus">+</button>
    <p v-if="dia!=0">Your value es {{ dia }}</p>
    <p v-else>Numero es 0</p>
    <p v-show="check">How you get here</p>
    <img :src="imagen1" alt=""/>
    <img :src="image2" alt=""/>
</div>
</template>

<script setup>
import { ref,computed } from 'vue';
import image2 from "./assets/image.png"

const imagen1 = "https://assets.pokemon.com/assets/cms2/img/pokedex/full/025.png";
const dia = ref(0);
const plus = () => {
    dia.value++;
    if(dia.value==10){
        console.log(dia.value)
    }
};
const menos = () => {
    dia.value--;

    if(dia.value<0){
        console.log("This calue es menor de 0 ")

    }
    
};

const check=computed(()=>{
    return dia.value===0;
})
</script>

<style lang="scss"></style>


</script>


