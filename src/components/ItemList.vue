<script setup>
import { ref } from "vue";

const items = ref([
  { name: "たまご", price: 100 },
  { name: "りんご", price: 160 },
]);
const newItemName = ref("");
const newItemPrice = ref(0);

const addItem = () => {
  if (newItemName.value != "") {
    if (newItemPrice.value != 0) {
      items.value.push({ name: newItemName.value, price: newItemPrice.value });
      newItemName.value = "";
      newItemPrice.value = 0;
    } else {
      alert("商品の価格を入れてください。");
    }
  } else {
    if (newItemPrice.value != 0) {
      alert("商品の名前を入れてください。");
    } else {
      alert("商品の名前と価格を入れてください。");
    }
  }
};
</script>

<template>
  <div>ItemList</div>
  <div v-for="item in items" :key="item.name">
    <div class="item" :class="{ over500: item.price >= 500 }">
      <div class="name">名前： {{ item.name }}</div>
      <div class="price">{{ item.price }} 円</div>
      <div v-if="item.price >= 10000">高額商品</div>
    </div>
  </div>
  <div>
    <label>
      名前
      <input v-model="newItemName" type="text" />
    </label>
    <label>
      価格
      <input v-model="newItemPrice" type="text" />
    </label>
    <button @click="addItem">add</button>
  </div>
</template>

<style>
.over500 {
  color: red;
}
</style>
