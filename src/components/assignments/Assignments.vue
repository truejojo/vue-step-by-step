<script>
import AssignmentList from "./AssignmentList.vue";
import AssignmentCreate from "./AssignmentCreate.vue";

export default {
  components: { AssignmentList, AssignmentCreate },

  data() {
    return {
      assignments: [
        { name: "Finish project", complete: false, id: 1, tag: "math" },
        { name: "Read Chapter 4", complete: false, id: 2, tag: "science" },
        { name: "Turn in Homework", complete: false, id: 3, tag: "math" },
      ],
    };
  },

  computed: {
    filters() {
      return {
        inProgress: this.assignments.filter(
          (assignment) => !assignment.complete
        ),
        completed: this.assignments.filter((assignment) => assignment.complete),
      };
    },
  },

  methods: {
    add(name) {
      this.assignments.push({
        name: name,
        completed: false,
        id: this.assignments.length + 1,
        tag: "database"
      });
    },
  },
};
</script>

<template>
  <section>
    <AssignmentList v-if="filters.inProgress.length"
      :assignments="filters.inProgress"
      title="In Progress"
    ></AssignmentList>
    <AssignmentList v-if="filters.completed.length"
      :assignments="filters.completed"
      title="Completed"
    ></AssignmentList>

    <AssignmentCreate @add="add"></AssignmentCreate>
  </section>
</template>
