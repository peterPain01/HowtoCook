<template >
    <header class="bg-black shadow text-white font-semibold h-16 flex justify-between items-stretch px-4
                   ">
        <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full">
                <div class="flex flex-row gap-2">
                    <img alt="Logo" class="inline h-8" width="32" height="32"
                    src="//global-web-assets.cpcdn.com/assets/logo_circle-d106f02123de882fffdd2c06593eb2fd33f0ddf20418dd75ed72225bdb0e0ff7.png">
                <img alt="Logo" class="mt-xs h-8 xs:inline" height="32" width="80"
                    src="//global-web-assets.cpcdn.com/assets/logo_text-da02013e64b510c60b109001fc44bcb7195f9e3105287817103b6cff4f8e0563.png">
                </div>
        </router-link>
        <div class="flex items-center gap-2">
            <router-link :to="{ name: 'byName' }"
                class="inline-flex items-center px-2 h-full transition-colors hover:bg-yellow-400">
                Search Meals
            </router-link>

            <router-link :to="{ name: 'byLetter' }"
                class="inline-flex items-center px-2 h-full transition-colors hover:bg-yellow-400">
                Meals by Letter
            </router-link>

            <router-link :to="{ name: 'byIngredient' }"
                class="inline-flex items-center px-2 h-full transition-colors hover:bg-yellow-400">
                Meals By Ingredients
            </router-link>
        </div>
    </header>
</template>
