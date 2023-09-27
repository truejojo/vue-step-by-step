<script setup>
import { ref, computed, provide } from "vue";
import AssignmentsList from "./AssignmentsList.vue";
import AssignmentCreate from "./AssignmentCreate.vue";

const assignments = ref([
  { name: "Finish project", complete: false, id: 1, tag: "math" },
  { name: "Read Chapter 4", complete: true, id: 2, tag: "programming" },
  { name: "Turn in Homework", complete: false, id: 3, tag: "database" },
  { name: "Lets's work...", complete: false, id: 4, tag: "math" },
]);

// const inProgress = computed(() =>
//   assignments.value.filter((assignment) => !assignment.complete)
// );

// const completed = computed(() =>
//   assignments.value.filter((assignment) => assignment.complete)
// );

const toggleComplete = (assignment) => {
  console.log(`assignment: ${assignment.id}`);
  assignment.complete = !assignment.complete;
};
provide("toggleComplete", toggleComplete);

const add = (name) => {
  assignments.value.push({
    id: Math.random(),
    name,
    complete: false,
    tag: "math",
  });
};
const filters = computed(() => {
  return {
    inProgress: assignments.value.filter((assignment) => !assignment.complete),
    completed: assignments.value.filter((assignment) => assignment.complete),
  };
});
</script>

<template>
  <AssignmentsList :assignments="filters.inProgress" title="In progress" />
  <AssignmentsList :assignments="filters.completed" title="Completed" />

  <AssignmentCreate @add="add" />
</template>

<style></style>
