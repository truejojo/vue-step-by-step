<script setup>
import { ref, onMounted } from "vue";

const greeting = ref("Hi there");

onMounted(() => {
  setTimeout(() => {
    greeting.value = "MOIN!!!";
  }, 3000);
});
</script>

<template>
    <label>
      <input type="text" v-model="greeting" />
      <p class="pt-2">{{ greeting }}</p>
    </label>
</template>
