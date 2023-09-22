<script setup>
defineProps({
  assignment: Object,
  toggleComplete: Function,
})
</script>

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
