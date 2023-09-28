<script setup></script>

<template>
  <section>
    <header v-if="$slots.heading" class="d-flex justify-content-between">
      <slot name="heading" />
    </header>

    <div v-if="$slots.assignmentTags" class="me-2 mb-3">
      <slot name="assignmentTags" />
    </div>

    <ul
      v-if="$slots.assignment"
      class="border border-secondary list-unstyled mb-4"
    >
      <slot name="assignment" />
    </ul>
    <slot></slot>
  </section>
</template>

<style></style>
