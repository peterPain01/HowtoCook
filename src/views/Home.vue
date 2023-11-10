<template>
    <div class="hero h-screen">
        <!-- Hero Home -->
        <div class="overlay"></div>
        <div class="flex hero-media">
            <!-- Hero Content -->
            <div class="hero-content flex justify-center items-center flex-col gap-8">
                <p class="text-3xl text-yellow-300 font-landing">Just Taste It</p>
                <p class="font-bold text-7xl text-white font-landing text-center">Cooking is our hobby</p>
                <p class="text-white text-center text-lg font-bold 
                            w-64">We create a website to share over 1000 recipes with everyone who loves cooking.</p>
            </div>
        </div>
    </div>
    <div class="mt-20">
        <div >
            <h1 class="text-center text-4xl font-bold"> </h1>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">

            </div>
        </div>
        <!--  line break -->
        <div>

        </div>
    </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store/';
import axiosClient from '../axiosClient.js'


const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
const ingredients = ref([]);
const meals = [{}];  

onMounted(async () => {
    const res = await axiosClient.get('/list.php?i=list')
    console.log(res.data);
    ingredients.value = res.data;
})
</script>

<style scoped>
.hero {
    position: relative;
}

.hero-media {
    width: 100%;
    height: 100%;
    background-image: url("../assets/img/VegNews.GordonRamsey.jpg");
    /* background-repeat: no-repeat; */
    justify-content: center;
    align-items: center;
}

.overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    background-color: #15141446;
}

.hero-content {
    width: fit-content;
    height: fit-content;
    transform: translateY(-62px);
}

img {
    width: 100%;
    height: 100%;
}
</style>


