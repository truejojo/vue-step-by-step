<script>
export default {
  props: {
    initialTags: Array,
    currentTag: String,
  },

  computed: {
    tags() {
      return ["all", ...new Set(this.initialTags)];
    },
  },
};
</script>

<template>
  <div class="me-2 mb-3">
    <small
      @click="$emit('update:currentTag', tag)"
      v-for="tag in tags"
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
