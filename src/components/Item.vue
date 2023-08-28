<script setup>
import { computed } from "vue";

const props = defineProps({
  item: Object
});

const { category, description, image, price, rating, title } = props.item;

const computedDescription = computed(() => {
  return description.length > 150 ? description.substring(0, 150) + '...' : description;
});
</script>

<template>
  <div class="item">
    <div class="item__category">
      {{ category }}
    </div>
    <div class="item__title">
      {{ title }}
    </div>
    <div class="item__img">
      <img :src="image" alt="item">
    </div>
    <div class="item__price">
      {{ price }}$
    </div>
    <div class="item__description">
      {{ computedDescription }}
    </div>
    <div class="item__rating">
      Rating {{ rating.rate }} (votes {{ rating.count }})
    </div>
    <div class="item__buttons">
      <button>To cart</button>
      <button>Buy</button>
    </div>
  </div>
  <br>
</template>

<style scoped>
.item {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 250px;
  height: 450px;
  padding: 10px;
  box-shadow: 2px 2px 5px #d1d3d3;
}
.item:hover {
  cursor: pointer;
  box-shadow: 4px 4px 10px #d1d3d3;
}
.item__category {
  font-size: 10px;
}
.item__title {
  font-weight: bold;
  height: 100px;
}
.item__img img {
  height: 100px;
}
.item__price {
  margin: 10px 0;
  font-weight: bold;
}
.item__description {
  height: 80px;
  font-size: 12px;
}
.item__rating {
  font-size: 14px;
  margin: 10px 0;
}
.item__buttons {
  display: flex;
  justify-content: space-around;
}
</style>
