<template>
  <div>
    <h1>Lifecycle</h1>
    {{ sayHello() }}
    <ul>
      <li>countC: {{ countC }}</li>
      <li>countD: {{ countD }}</li>
    </ul>
    <button @click="handleChange">Increase</button>
    <p>Hàm tính toán bình thường: {{ calculatorC() }}</p>
    <p>Hàm dùng computed: {{ calculatorD }}</p>
  </div>
</template>

<script setup>
import {
  computed,
  onBeforeMount,
  onBeforeUnmount,
  onBeforeUpdate,
  onMounted,
  onUnmounted,
  onUpdated,
  ref,
} from "vue";
const props = defineProps(["count"]);
const countC = ref(0);
const countD = ref(0);
const isShow = ref(true);

onBeforeMount(() => {
  console.log("Hook onBeforeMount được gọi");
});

const sayHello = () => {
  console.log("Hello");
};

onMounted(() => {
  console.log("Hook onMounted được gọi");
  // Nơi gọi API lấy data dữ liệu gắn vào DOM
});

const calculatorC = () => {
  return countC.value ** 2;
};

const calculatorD = computed(() => {
  return countD.value ** 2;
});

// Giai đoạn update
onBeforeUpdate(() => {
  console.log("Hook onBeforeUpdate được gọi");
});
onUpdated(() => {
  console.log("Hook onUpdated được gọi");
});

const handleChange = () => {
  countC.value++;
};

onBeforeUnmount(() => {
  console.log("Hook onBeforeUnmount được gọi");
});

onUnmounted(() => {
  console.log("Hook onUnMounted được gọi");
});
</script>

<style></style>