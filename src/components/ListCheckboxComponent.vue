<script setup>
import { ref, computed } from "vue";
const assignments = ref([
  { name: "Finish project", complete: false, id: 1 },
  { name: "Read Chapter 4", complete: true, id: 2 },
  { name: "Turn in Homework", complete: false, id: 3 },
]);

const inProgressAssignments = computed(() =>
  assignments.value.filter((assignment) => !assignment.complete)
);

const completeAssignments = computed(() =>
  assignments.value.filter((assignment) => assignment.complete)
);

const toggleComplete = (assignment) => {
  assignment.complete = !assignment.complete;
};
</script>

<template>
  <section v-if="inProgressAssignments.length">
    <h2>Assignments in progress</h2>
    <ul class="list-unstyled">
      <li v-for="assignment in inProgressAssignments" :key="assignment.id">
        <input
          type="checkbox"
          :checked="assignment.complete"
          @input="toggleComplete(assignment)"
        />
        {{ assignment.name }}
      </li>
    </ul>
  </section>
  <section v-if="completeAssignments.length">
    <h2>Assignments complete</h2>
    <ul class="list-unstyled">
      <li v-for="assignment in completeAssignments" :key="assignment.id">
        <input
          type="checkbox"
          :checked="assignment.complete"
          @input="toggleComplete(assignment)"
        />
        {{ assignment.name }}
      </li>
    </ul>
  </section>
</template>

<style></style>
