<script setup>
import { computed } from "vue";

const props = defineProps({
  initialTags: {
    type: Array,
    required: true,
  },
  currentTag: {
    type: String,
    required: true,
  },
});

const tags = computed(() => ["all", ...new Set(props.initialTags)]);
</script>

<template>
  <div class="me-2 mb-3">
    <small
      v-for="tag in tags"
      @click="$emit('update:currentTag', tag)"
      class="border border-secondary border-1 rounded px-3 py-0 text-uppercase me-1"
      :class="{
        'border-info text-info': tag === currentTag,
      }"
    >
      {{ tag }}
    </small>
  </div>
</template>

<style></style>
