<script setup>
import { ref, computed } from "vue";
import AssignmentList from "./AssignmentList.vue";
import AssignmentCreate from "./AssignmentCreate.vue";

const assignments = ref([
  { name: "Finish project", complete: false, id: 1, tag: "math" },
  { name: "Read Chapter 4", complete: false, id: 2, tag: "science" },
  { name: "Turn in Homework", complete: false, id: 3, tag: "math" },
]);

const filters = computed(() => {
  return {
    inProgress: assignments.value.filter((assignment) => !assignment.complete),
    completed: assignments.value.filter((assignment) => assignment.complete),
  };
});

const add = (name) => {
  assignments.value.push({
    name,
    completed: false,
    id: Math.random(),
    tag: "database",
  });
};
</script>

<template>
  <section>
    <AssignmentList
      v-if="filters.inProgress.length"
      :assignments="filters.inProgress"
      title="In Progress"
    ></AssignmentList>
    <AssignmentList
      v-if="filters.completed.length"
      :assignments="filters.completed"
      title="Completed"
    ></AssignmentList>

    <AssignmentCreate @add="add"></AssignmentCreate>
  </section>
</template>
