<template>
    <div class="flex flex-col p-8">
       
    </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store/';
import axiosClient from '../axiosClient.js'


const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
const ingredients = ref([]); 

onMounted(async () => {
    const res = await axiosClient.get('/list.php?i=list')
    console.log(res.data);
    ingredients.value = res.data; 
})
</script>

<style scoped></style>
