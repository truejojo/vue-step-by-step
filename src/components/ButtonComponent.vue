<script setup>
import { ref, computed } from "vue";

const isActive = ref(false);

const toggleColor = () => (isActive.value = !isActive.value);

const getColor = computed(() => (isActive.value ? "text-red" : "text-blue"));
</script>

<template>
  <button
    @click="toggleColor()"
    :class="getColor"
    class="btn btn-outline-success border-3 text-uppercase fw-bold"
  >
    Change Text Color
  </button>
</template>

<style scoped>
.text-red {
  color: red;
}

.text-blue {
  color: blue;
}
</style>
