<script setup>
import { ref, computed } from "vue";
import AssignmentPanel from "../../layouts/AssignmentPanel.vue";
import Assignment from "./Assignment.vue";
import AssignmentTags from "./AssignmentTags.vue";

const props = defineProps({
  assignments: {
    type: Array,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  canToggle: {
    type: Boolean,
    default: false,
  },
});
const emit = defineEmits(['toggle']);

const currentTag = ref("all");

const filteredAssignments = computed(() =>
  currentTag.value === "all"
    ? props.assignments
    : props.assignments.filter(
        (assignment) => assignment.tag === currentTag.value
      )
);

const assignmentsTags = computed(() =>
  props.assignments.map((assignment) => assignment.tag));
</script>

<template>
  <AssignmentPanel v-show="assignments.length">
    <template #heading>
      <h2 class="fw-bold mb-2">
        {{ title }}
        <span class="fw-normal">({{ assignments.length }})</span>
      </h2>
      <button
        v-show="canToggle"
        @click="emit('toggle')"
        class="btn btn-info btn-sm"
      >
        &times;
      </button>
    </template>

    <template #assignmentTags>
      <AssignmentTags
        v-model:currentTag="currentTag"
        :initial-tags="assignmentsTags"
      ></AssignmentTags>
    </template>

    <template #assignment>
      <Assignment
        v-for="assignment in filteredAssignments"
        :key="assignment.id"
        :assignment="assignment"
      ></Assignment>
    </template>

    <slot></slot>
  </AssignmentPanel>
</template>
