<script setup>
import BorderLayout from "./layouts/BorderLayout.vue";
import InputComponent from "./components/InputComponent.vue";
import ButtonComponent from "./components/ButtonComponent.vue";
import ListCheckboxComponent from "./components/ListCheckboxComponent.vue";
</script>

<template>
  <div class="container">
    <BorderLayout>
      <InputComponent />
    </BorderLayout>
    <BorderLayout>
      <ButtonComponent />
    </BorderLayout>
    <BorderLayout>
      <ListCheckboxComponent />
    </BorderLayout>
  </div>
</template>

<style scoped></style>
