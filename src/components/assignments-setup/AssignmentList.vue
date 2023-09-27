<script setup>
import { ref, computed } from "vue";
import Assignment from "./Assignment.vue";
import AssignmentTags from "./AssignmentTags.vue";

const props = defineProps({
  assignments: {
    type: Array,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
});

const currentTag = ref("all");

const filteredAssignments = computed(() =>
  currentTag.value === "all"
    ? props.assignments
    : props.assignments.filter(
        (assignment) => assignment.tag === currentTag.value
      )
);

const getAssignmentsTags = () =>
  props.assignments.map((assignment) => assignment.tag);
// const assignmentsTags = computed(() =>
//   props.assignments.map((assignment) => assignment.tag));
</script>

<template>
  <section v-if="assignments.length">
    <h2 class="fw-bold mb-2">
      {{ title }}
      <span class="fw-normal">({{ assignments.length }})</span>
    </h2>

    <AssignmentTags
      v-model:currentTag="currentTag"
      :initial-tags="getAssignmentsTags()"
    ></AssignmentTags>
    <ul class="border border-secondary list-unstyled mb-4">
      <Assignment
        v-for="assignment in filteredAssignments"
        :key="assignment.id"
        :assignment="assignment"
      ></Assignment>
    </ul>
  </section>
</template>
