<script setup>
import Dropdown from './components/Dropdown.vue';
import StarRating from './components/StarRating.vue';

const dropdown_items = ['Links', 'Account', 'Something', 'Else'];
const star_amount = 5;

</script>

<template>
  <main class="main">
    <h1>Hello</h1>
    <Dropdown :items="dropdown_items"></Dropdown>
    <StarRating :stars="star_amount"></StarRating>
  </main>
</template>

<style scoped>
.main{
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
