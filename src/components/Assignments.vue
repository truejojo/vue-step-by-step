<script setup>
import { ref, computed, provide } from "vue";
import AssignmentsList from "./AssignmentsList.vue";

const assignments = ref([
  { name: "Finish project", complete: false, id: 1 },
  { name: "Read Chapter 4", complete: true, id: 2 },
  { name: "Turn in Homework", complete: false, id: 3 },
]);

const inProgress = computed(() =>
  assignments.value.filter((assignment) => !assignment.complete)
);

const completed = computed(() =>
  assignments.value.filter((assignment) => assignment.complete)
);

const toggleComplete = (assignment) => {
  assignment.complete = !assignment.complete;
};
provide('toggleComplete', toggleComplete);
// const filters = computed(() => {
//   return {
//     inProgress: this.assignments.filter((assignment) => !assignment.complete),
//     completed: this.assignments.filter((assignment) => assignment.complete),
//   };
// });
</script>

<template>
  <AssignmentsList
    :assignments="inProgress"
    title="In progress"
  />
  <AssignmentsList
    :assignments="completed"
    title="Completed"
  />
</template>

<style></style>
