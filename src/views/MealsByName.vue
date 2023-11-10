<template>
    <div class="p-8">
        <h1 class="text-4xl text-orange-500 my-2 font-bold text-center">{{ title }}</h1>
        <input type="text" v-model="keyword" class="rounded border-2 border-gray-200 w-full" placeholder="Search for Meals"
            @change="searchMeals" />
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
        <div v-for="meal of meals" :key="meal.idMeal"
            class="bg-white shadow rounded-xl flex flex-col justify-center items-center ">
            <router-link class="custom-link" :to="{name: 'mealDetails', params: {id: meal.idMeal}}" >
                <img :src="meal.strMealThumb" :alt="meal.srtMeal" class="rounded-t-xl w-full h-48 object-cover">
            </router-link>
            <h3 class="py-3 text-center font-bold">{{ meal.strMeal }}</h3>
            <div class="flex flex-wrap justify-center items-center ">
                <p class="text-center mb-3 basis-full w-24">Lorem ipsum, dolor sit amet consectetur adipisicing elit. A, alias.</p>
                <a :href="meal.strYoutube" target="_blank">
                    <button class="mb-2">
                        <span class="icon"><svg fill="none" height="33" viewBox="0 0 120 120" width="33"
                                xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="m120 60c0 33.1371-26.8629 60-60 60s-60-26.8629-60-60 26.8629-60 60-60 60 26.8629 60 60z"
                                    fill="#cd201f"></path>
                                <path
                                    d="m25 49c0-7.732 6.268-14 14-14h42c7.732 0 14 6.268 14 14v22c0 7.732-6.268 14-14 14h-42c-7.732 0-14-6.268-14-14z"
                                    fill="#fff"></path>
                                <path d="m74 59.5-21 10.8253v-21.6506z" fill="#cd201f"></path>
                            </svg></span>
                        <span class="text1">Cooking</span>
                        <span class="text2">Watch</span>
                    </button>
                </a>
            </div>
        </div>
    </div>
</template>

<script setup>

import { ref, computed, onMounted } from 'vue';
import store from '../store';
import {useRoute} from 'vue-router'

const keyword = ref('');
const title = ref('Search Meals by Name');
const meals = computed(() => store.state.searchedMeals)
const route = useRoute(); 

function searchMeals() {
    store.dispatch('searchMeals', keyword.value)
}

onMounted(() => {
    keyword.value = route.params.name; 
    if(keyword.value){ 
        searchMeals(); 
    }
})
</script>

<style scoped>

.custom-link{ 
    display: block;
    width: 100%;
}

button {
    position: relative;
    width: 130px;
    height: 35px;
    border-radius: 30px;
    background-color: white;
    border: 1px #cd201f solid;
    overflow: hidden;
}

.text1 {
    text-align: center;
    font-size: 15px;
    font-weight: 600;
    margin-left: 22%;
}

.text2 {
    text-align: center;
    position: absolute;
    top: 15%;
    left: -50px;
    font-weight: 700;
    font-size: 14px;
    color: white;
}

.icon {
    position: absolute;
    top: 0;
    left: 0;
    transition: transform 0.5s;
}

.icon::before {
    position: absolute;
    left: -100px;
    top: 0;
    z-index: -1;
    content: '';
    width: 130px;
    height: 33px;
    border-radius: 30px;
    background-color: #cd201f;
}

button:hover .icon {
    transform: translateX(96px);
    transition: transform 0.5s;
}

button:hover .text2 {
    transform: translateX(100px);
    transition: transform 0.6s;
}

button:active {
    transform: scale(1.03);
}
</style>