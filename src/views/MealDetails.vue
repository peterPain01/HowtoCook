<template>
    <div class="bg-gray-200 flex custom-div">
        <div class="w-2/3 flex mt-4 justify-center items-center flex-col">
            <div class="width-500"><img class="custom-img rounded-md" :src="meal.strMealThumb" alt="strMeal"></div>
            <div class="width-500 bg-white rounded-md mt-4">
                <h1 class="p-4 text-start font-semibold leading-tight text-4xl text-stone-700">{{ meal.strMeal }}</h1>
                <h1>{{ }}</h1>
            </div>

            <div class="width-500 bg-white rounded-md mt-4">
                <h2 class="p-4 pb-0 text-start font-semibold leading-tight text-2xl text-stone-700">Ingredients</h2>
                <div class="mt-6">
                    <ul>
                        <template v-for="index in 20">
                            <li class="px-4 py-1 border-b-2 border-dashed" v-if="meal[`strIngredient${index + 1}`]">
                                {{ meal[`strIngredient${index + 1}`] + ": " + meal[`strMeasure${index + 1}`] }}</li>
                        </template>
                    </ul>
                </div>
            </div>
 
            <div class="width-500 bg-white rounded-md mt-4">
                <h2 class="p-4 pb-0 text-start font-semibold leading-tight text-2xl text-stone-700">Instruction</h2>
                <div class="mt-6">
                    <p class="p-4">{{ meal.strInstructions }}</p>
                </div>
            </div>

            <div class="width-500 bg-white rounded-md mt-4 flex flex-col justify-start">
                <h2 class="p-4 pb-0 text-start font-semibold leading-tight text-2xl text-stone-700">Video Guide</h2>
                <div class="mt-6">
                    <iframe class="w-full h-96 rounded-xl" :src="iframeURL"
                        title="Rick Astley - Never Gonna Give You Up (Official Music Video)" frameborder="0"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                        allowfullscreen></iframe>
                </div>
            </div>
        </div>

        <div class="w-1/3 mt-4">
            <div class="w-80 bg-white rounded-md shadow-md sticky top-0">
                <div class=" flex flex-col gap-2 justify-center items-center py-4">
                    <button
                        class="w-72 h-9 border-2 border-solid border-amber-500 rounded-md font-bold text-orange-400">Save</button>
                    <button class="w-72 h-9 border-2 border-solid border-zinc-300 rounded-md">Share</button>
                    <button class="w-72 h-9 border-2 border-solid border-zinc-300 rounded-md">Print</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';

const meal = ref({})
const route = useRoute();
const youtubeEmbed = '/embed/'
const iframeURL = ref('')
onMounted(() => {
    axiosClient.get(`lookup.php?i=${route.params.id}`)
        .then(({ data }) => {
            return meal.value = data.meals[0] || [];
        })
        .then(({ }) => {
            if (meal.value.strYoutube) {
                iframeURL.value = (meal.value.strYoutube.split('/watch?v=')
                [0] + youtubeEmbed + meal.value.strYoutube.split('/watch?v=')[1]);
            }
            else {
                iframeURL.value = "https://www.youtube.com/embed/dQw4w9WgXcQ";
            }
        })  
})

</script>

<style scoped>
.bg-gray-200 {
    --tw-bg-opacity: 1;
    background-color: #f8f6f2;
}

.width-500 {
    width: 700px;
}

.custom-img {
    width: 100%;
    height: 500px;
    object-fit: cover;
}

.custom-div {
    width: 1170px;
    min-width: calc(100% - 60px);
    margin: 0 auto;
}
</style>


