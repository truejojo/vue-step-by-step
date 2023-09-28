<script setup>
import { ref, computed, onMounted } from "vue";
import axios from "axios";
import AssignmentList from "./AssignmentList.vue";
import AssignmentCreate from "./AssignmentCreate.vue";

const assignments = ref([
  { name: "Finish project", complete: false, id: 1, tag: "math" },
  { name: "Read Chapter 4", complete: false, id: 2, tag: "science" },
  { name: "Turn in Homework", complete: false, id: 3, tag: "math" },
]);

/* http://localhost:3000/assignments */

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

const showCompleted = ref(true);
const toggleShowCompleted = () => (showCompleted.value = !showCompleted.value);
</script>

<template>
  <section class="row">
    <div class="col-12 col-md-6">
      <AssignmentList :assignments="filters.inProgress" title="In Progress">
        <AssignmentCreate @add="add"></AssignmentCreate>
      </AssignmentList>
    </div>
    <div class="col-12 col-md-6" v-show="showCompleted">
      <AssignmentList
        :assignments="filters.completed"
        title="Completed"
        canToggle
        @toggle="toggleShowCompleted()"
      >
      </AssignmentList>
    </div>
  </section>
</template>
