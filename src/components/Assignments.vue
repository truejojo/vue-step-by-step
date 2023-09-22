<script setup>
import { ref, computed } from "vue";
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
    :toggleComplete="toggleComplete"
  />
  <AssignmentsList
    :assignments="completed"
    title="Completed"
    :toggleComplete="toggleComplete"
  />
</template>

<style></style>
