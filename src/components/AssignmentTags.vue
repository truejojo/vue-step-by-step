<script setup>
import { computed } from "vue";

const { initialTags, currentTag } = defineProps({
  initialTags: Array,
  currentTag: String,
});

const tags = computed(() => [
  "all",
  ...new Set(initialTags),
  // ...new Set(assignments.map((assignment) => assignment.tag)),
]);
</script>

<template>
  <div>
    <small
      v-for="tag in tags"
      @click="$emit('update:currentTag', tag)"
      class="border border-1 rounded-1 text-uppercase px-2 me-2"
      :class="{
        'border-info text-info': tag === currentTag,
      }"
      >{{ tag }}</small
    >
  </div>
</template>

<style></style>
