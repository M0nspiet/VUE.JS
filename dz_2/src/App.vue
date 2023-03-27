<script setup>
  import { ref, reactive, computed } from "vue";
  import css from "./App.module.css";

  const text = ref("");
  const pass = "1234";
  const card = reactive({
    card1: "1c",
    card2: "c++",
    card3: "js",
  })
  function myHandler(event){
    text.value = event.target.value;
  }

  const variants = computed(() => ({
    [css.v1] : true,
    [css.v2] : text.value === "123",
  }));
</script>

<template>
  <header :class = "css.H1">Hello!</header>
  <input type="text" v-model="text"/>
  <div v-for="(value, key, index) in card" :key="index" v-if="text === '123'">
    <h1 :class="variants">{{ key }} : {{ value }} </h1>
  </div>
</template>