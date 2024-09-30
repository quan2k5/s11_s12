<script setup>
import {ref,computed} from 'vue'
const value1=ref(0)
const cartTotal=ref(0)
const handleAddCart=()=>{
    cartTotal.value += value1.value; 
    value1.value = 0;
}
const totalPrice = computed(() => cartTotal.value);
</script>
<template>
    <div>
        <input type="number" v-model="value1" >
        <button @click="handleAddCart">add cart</button>
        <div>Tong tien trog gio hang:{{totalPrice}}</div>
    </div>
</template>
<style scoped>
</style>
