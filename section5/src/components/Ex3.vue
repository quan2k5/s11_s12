<script setup>
import {ref} from 'vue'
const userRole=ref('admin');
</script>
<template>
    <div>
        <div v-if="userRole==='admin'">quyền hạn của bạn là admin</div>
        <div v-else-if="userRole==='user'">quyền hạn của bạn là user</div>
        <div v-else-if="userRole==='guest'">quyền hạn của bạn là guest</div>   
    </div>
</template>