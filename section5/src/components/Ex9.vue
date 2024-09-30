<script setup>
import {ref} from 'vue'
const gender=ref('Nam');
const handleRandom=()=>{
    let randomNumber=ref();
     randomNumber.value = Math.floor(Math.random() * 3);
     console.log(randomNumber.value);   
     if(randomNumber.value==0){
        gender.value='Nam'
     }
      if(randomNumber.value==1){
        gender.value='Nữ'
     }
      if(randomNumber.value==2){
        
        gender.value='khác'
     }
}
</script>
<template>
    <div>
        <button @click="handleRandom">random</button>
        <div>{{gender}}</div>
    </div>
</template>
<style scoped>
</style>
