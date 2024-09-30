<script setup>
import Ex1 from './components/Ex1.vue'
import Ex2 from './components/Ex2.vue'
import Ex3 from './components/Ex3.vue'
import Ex4 from './components/Ex4.vue'
import Ex5 from './components/Ex5.vue'
import Ex6 from './components/Ex6.vue'
import Ex7 from './components/Ex7.vue'
import Ex8 from './components/Ex8.vue'
import Ex9 from './components/Ex9.vue'
import Ex10 from './components/Ex10.vue'
const isCheck=true;
const isShow=true;
const students=[
  {
    id:1,
    name:'phuonng thao',
  },
  {
    id:2,
    name:'quan le',
  }
]
const person={

}
</script>

<template>
<div>
  <h3>Condition và list render</h3>
  <ul>
    <li>v if</li>
    <li>v else</li>
    <li>v else if</li>
    <li>v show</li>
  </ul>
  <p>v-if</p>
  <p v-if="isCheck">hiển thị vif và thỏa mãn điều kiện hoàn thành</p>
  <p v-else>hiển thị v else</p>
  <p>*************</p>
  <p>V-show</p>
  <p v-show="isShow">element đc hiển thị nếu đk vshow thỏa mãn</p>
  <p>***************</p>
  <p>rendering</p>
  <li v-for="std in students" :key="std.id">{{std.name}}</li>
  <ex-1></ex-1>
  <ex-2></ex-2>
  <ex-3></ex-3>
  <ex-4></ex-4>
  <ex-5></ex-5>
  <ex-6></ex-6>
  <ex-7></ex-7>
  <ex-8></ex-8>
  <ex-9></ex-9>
  <ex-10></ex-10>
</div> 
</template>
<style scoped>
</style>
