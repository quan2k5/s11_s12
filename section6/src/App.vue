<script setup>
import {ref,reactive,computed} from 'vue';
const valueInput=ref('');
let jobs=reactive(JSON.parse(localStorage.getItem('jobs'))||[[]])
const addJob=()=>{
  let job={
    name:valueInput.value,
    status:false,
    id:Math.ceil(Math.random()*100000)
  }
  jobs.push(job);
  console.log("mang vhua danh sach cong viec job",jobs);
  localStorage.setItem("jobs",JSON.stringify(jobs));
  valueInput.value="";
  
}
const completedJob=computed(()=>{
  return jobs.reduce((acc,currentValue)=>{
    return acc+Number(currentValue.status)
  },0)
})
const handleDelete=(job)=>{
  const index=jobs.findIndex((item)=>{
    return item.id===job.id;
  });
  jobs.splice(index,1);
  localStorage.setItem("jobs",JSON.stringify(jobs));
}
</script>
<template>
<div>
  <input type="text" v-model="valueInput" placeholder="Them noi ung cong viec">
  <br>
  <button @click='addJob'>them cong viec</button>
  <div class="list">
    <h1>Danh sach cong viec</h1> 
    <ul>
        <li :key="job.id" v-for="job in jobs">
          <input type="checkbox" v-model="job.status">
          <span :class="{success:job.status}">{{job.name}}</span> /
          <button @click="handleDelete(job)">Xoa</button>
        </li>
    </ul>
  </div>
  <h4>So cong viec hoan thanh{{completedJob}}</h4>
</div>
</template>
<style scoped>
.success{
  text-decoration: line-through;
}
</style>
