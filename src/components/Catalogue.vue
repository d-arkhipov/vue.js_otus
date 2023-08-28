<script setup>
import Item from "./Item.vue";

const url = 'https://fakestoreapi.com/products';
const response = await fetch(url);
let items = [];

if (response.ok) {
  items = await response.json();
} else {
  alert(`An HTTP error (${response.status}) occurred, while receiving the list of products.`);
}
</script>

<template>
  <div class="catalogue">
    <Item v-for="item in items" :key="item.id" :item="item"/>
  </div>
</template>

<style scoped>
.catalogue {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
