<script>
export default {
  props: {
    assignment: Object,
  },
};
</script>

<template>
  <li>
    <label class="p-1 fs-4">
      <input type="checkbox" v-model="assignment.complete" class="me-2" />
      {{ assignment.name }}
    </label>
  </li>
</template>

<style></style>
