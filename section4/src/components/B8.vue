<script setup>
import { ref, computed } from 'vue';
const products = ref([
  { name: 'Mền Mền Loại 1', quantity: 3 },
  { name: 'Mền Mền Loại 2', quantity: 5 },
  { name: 'Mền Mền Loại 3', quantity: 1 }
]);
const increaseQuantity = (product) => {
  product.quantity++;
};
const totalQuantity = computed(() => {
  return products.value.reduce((total, product) => total + product.quantity, 0);
});
</script>
<template>
  <div>
    <h2>Giỏ hàng</h2>
    <ul>
      <li v-for="(product, index) in products" :key="index">
        {{ product.name }} - Số lượng: {{ product.quantity }}
        <button @click="increaseQuantity(product)">Tăng số lượng</button>
      </li>
    </ul>
    <p>Tổng số lượng sản phẩm: {{ totalQuantity }}</p>
  </div>
</template>