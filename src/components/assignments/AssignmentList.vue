<script>
import Assignment from "./Assignment.vue";
import AssignmentTags from "./AssignmentTags.vue";

export default {
  components: { Assignment, AssignmentTags },
  props: {
    assignments: Array,
    title: String,
  },

  props: {
    assignments: Array,
    title: String,
  },

  data() {
    return {
      currentTag: "all",
    };
  },

  computed: {
    filteredAssignments() {
      if (this.currentTag === "all") {
        return this.assignments;
      }

      return this.assignments.filter((a) => a.tag === this.currentTag);
    },
  },
};
</script>

<template>
  <section v-show="assignments.length">
    <h2 class="fw-bold mb-2">
      {{ title }}
      <span class="fw-normal">({{ assignments.length }})</span>
    </h2>

    <AssignmentTags
      v-model:currentTag="currentTag"
      :initial-tags="assignments.map((a) => a.tag)"
    ></AssignmentTags>
    <ul class="border border-secondary list-unstyled mb-4">
      <Assignment
        v-for="assignment in filteredAssignments"
        :key="assignment.id"
        :assignment="assignment"
      ></Assignment>
    </ul>
  </section>
</template>
