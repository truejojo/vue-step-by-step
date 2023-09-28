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
const emit = defineEmits(["update:currentTag"]);

const tags = computed(() => ["all", ...new Set(props.initialTags)]);
</script>

<template>
  <small
    v-for="tag in tags"
    @click="emit('update:currentTag', tag)"
    class="border border-secondary border-1 rounded px-3 py-0 text-uppercase me-1"
    :class="{
      'border-info text-info': tag === currentTag,
    }"
  >
    {{ tag }}
  </small>
</template>

<style></style>
