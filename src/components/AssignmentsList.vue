<script setup>
import { ref, computed } from "vue";
import Assignment from "./Assignment.vue";
import AsssignmentTags from "./AssignmentTags.vue";

const { assignments, title } = defineProps({
  assignments: Array,
  title: String,
});

const currentTag = ref("all");

const filteredAssignments = computed(() => {
  return currentTag.value === "all"
    ? assignments
    : assignments.filter((assignment) => assignment.tag === currentTag.value);
});
</script>

<template>
  <section v-if="assignments.length">
    <h2>
      {{ title }} <small>({{ assignments.length }})</small>
    </h2>
    <AsssignmentTags
      v-model:currentTag="currentTag"
      :initialTags="assignments.map((assignment) => assignment.tag)"
    />
    <ul class="list-unstyled">
      <Assignment
        v-for="assignment in filteredAssignments"
        :key="assignment.id"
        :assignment="assignment"
      />
    </ul>
  </section>
</template>

<style></style>
