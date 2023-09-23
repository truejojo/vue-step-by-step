<script setup>
import Assignment from "./Assignment.vue";

defineProps({
  assignments: Array,
  title: String,
});
</script>

<template>
  <section v-if="assignments.length">
    <h2>{{ title }}</h2>
    <ul class="list-unstyled">
      <Assignment
        v-for="assignment in assignments"
        :key="assignment.id"
        :assignment="assignment"
      />
    </ul>
  </section>
</template>

<style></style>
