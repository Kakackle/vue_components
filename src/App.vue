<script setup>
import Dropdown from './components/Dropdown.vue';

const dropdown_items = ['Links', 'Account', 'Something', 'Else'];

</script>

<template>
  <h1>Hello</h1>
  <Dropdown :items="dropdown_items"></Dropdown>
</template>

<style scoped>
</style>
