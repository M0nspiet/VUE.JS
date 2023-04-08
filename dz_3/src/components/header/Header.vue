<script setup>
import { ref, reactive, computed, onMounted, onBeforeMount, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted, watch, watchEffect } from 'vue';
  const time = ref(Date.now());
  const timeIntervalId = ref(0);
  const card = reactive({
    card1: "1c",
    card2: "c++",
    card3: "js",
  });
  onMounted(() =>{
    timeIntervalId.value = setInterval(() => {
      time.value = Date.now();
    }, 100);
  });

  onUnmounted(() => {
    clearInterval(timeIntervalId.value);
  });
</script>


<template>
    <button><slot name = "slot_1"></slot>
    <p><slot name = "slot_2">{{ time }}</slot></p></button>
</template>

<style scoped>

</style>