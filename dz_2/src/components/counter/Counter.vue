<script setup>
import { reactive,ref,watchEffect, watch } from 'vue';

const counter = ref(0);
const date = ref(new Date().toLocaleDateString());

function counterHandler(event){
    counter.value++;
}

watch(
    {},
    ()=>{
        setInterval(() =>{
            date.value = new Date().toLocaleDateString();
        },1000);
    },
    {immediate:true}
)

</script>

<template>
    <button @click="counterHandler">counter {{ counter }}</button>
    <h1>{{ date }}</h1>
</template>

<style scoped></style>