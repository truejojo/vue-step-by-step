<script setup>
import { inject } from "vue";

defineProps({
  assignment: Object,
});
const toggleComplete = inject("toggleComplete");
</script>

<!-- TODO
funktioniert nicht mit v-model
-->
<template>
  <li>
    <input
      type="checkbox"
      :checked="assignment.complete"
      @input="toggleComplete(assignment)"
    />
    {{ assignment.name }}
  </li>
</template>

<style></style>
