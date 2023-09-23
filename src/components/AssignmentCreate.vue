<script setup>
import { ref } from "vue";

const emit = defineEmits(["add"]);
const newAssignment = ref("");

const addAssignment = () => {
  emit("add", newAssignment.value);
  newAssignment.value = "";
};
</script>

<template>
  <form @submit.prevent="addAssignment" class="d-flex align-items-center">
    <div class="border d-flex align-items-center">
      <input
        type="text"
        v-model="newAssignment"
        placeholder="New assignment..."
        class="p-1"
      />
      <button type="submit" class="btn btn-light border-0 rounded-0">
        Add
      </button>
    </div>
  </form>
</template>

<style></style>
