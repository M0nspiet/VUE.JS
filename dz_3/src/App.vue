<script setup>
  import { ref, reactive, computed, onMounted, onBeforeMount, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted, watch, watchEffect } from "vue";
  import css from "./App.module.css";
  import Header from "./components/header/Header.vue";

  const text = ref("");
  // const answer = ref("");
  // const answerImg = ref("");
  const card = reactive({
    card1: "1C",
    card2: "S++",
    card3: "js",
    card3: "python",
    card4: "LUA",
    card5: "Api",
  });

  watch(text,async () => {
    if (text.value.indexOf("?") === -1) {
      answer.value = "it's not question.";
      return;
    }
    const res = await fetch("https://yesno.wtf/api");
    const data = await res.json();
    answer.value = data.answer;
    answerImg.value = data.image;
  });
</script>

<template>
  <header :class = "css.H1">Hello!</header>
  <input type="text" v-model="text"/>
  <div v-for="(value, key, index) in card" :key="index" >
    <Header>
      <template #slot_1>
        {{ value }} 
      </template>
      <template #slot_2> 
        
      </template>
    </Header>
  </div>
  <!-- <p>{{ answer }}</p>
  <img v-if = "answerImg" :src="answerImg" :alt ="answer"> -->
</template>