<script setup>
import {ref} from 'vue';
import Lifecycle from "./components/Lifecycle.vue";
import Ex1 from './components/Ex1.vue'
import Ex2 from './components/Ex2.vue'
import Ex3 from './components/Ex3.vue'
import Ex4Parent from './components/Ex4Parent.vue'
import Ex5Parent from './components/Ex5Parent.vue'
import Ex6 from './components/Ex6.vue'
import Ex7 from './components/Ex7.vue'
import Ex8 from './components/Ex8.vue'
import Ex9 from './components/Ex9.vue'
import Ex10 from './components/Ex10.vue'
const check1=ref(true);
const activate=()=>{
  check1.value=!check1.value;
}
const handleMessage=(data)=>{
  console.log(data);
  
}
</script>

<template>
  <div>
    <h1>dfjfijvff</h1>
    <!-- <lifecycle></lifecycle> -->
    <p>Bài 1</p>
    <ex-1></ex-1>
    <p>Bài 2</p>
    <ex-2></ex-2>
    <p>Bài 3</p>
    <ex-3></ex-3>
    <p>Bài 4</p>
    <Ex4Parent></Ex4Parent>
    <p>Bài 5</p>
    <ex-5-parent></ex-5-parent>
    <p>Bài 6</p>
    <ex-6></ex-6>
    <p>Bài 7</p>
    <ex-7></ex-7>
    <p>Bài 8</p>
    <ex-8></ex-8>
    <p>Bài 9</p>
    <ex-9></ex-9>
    <p>Bài 10</p>
    <button @click="activate">Bài 10</button>
    <ex-10 v-if="check1" @checkad="handleMessage"></ex-10>
  </div>
</template>
<style scoped>
</style>