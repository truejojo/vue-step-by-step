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
      <ButtonComponent>toggle color</ButtonComponent>
      <ButtonComponent>click me</ButtonComponent>
      <ButtonComponent>send</ButtonComponent>
    </BorderLayout>
    <BorderLayout>
      <ListCheckboxComponent />
    </BorderLayout>
  </div>
</template>

<style>
  #app {
    min-height: 100vh;
    background-color: #222;
    color: #f5f5f5
  }
</style>
