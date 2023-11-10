<template>
    <footer class="bg-white rounded-lg shadow">
        <div class="w-full max-w-screen-xl mx-auto p-4 md:py-8">
            <div class="sm:flex sm:items-center sm:justify-between">
                <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full">
                    <div class="flex flex-row gap-2">
                        <img alt="Logo" class="inline h-8" width="32" height="32"
                            src="//global-web-assets.cpcdn.com/assets/logo_circle-d106f02123de882fffdd2c06593eb2fd33f0ddf20418dd75ed72225bdb0e0ff7.png">
                        <img alt="Logo" class="mt-xs h-8 xs:inline" height="32" width="80"
                            src="//global-web-assets.cpcdn.com/assets/logo_text-da02013e64b510c60b109001fc44bcb7195f9e3105287817103b6cff4f8e0563.png">
                    </div>
                </router-link>
                <ul class="flex flex-wrap items-center mb-6 text-sm font-medium text-gray-500 sm:mb-0 dark:text-gray-400">
                    <li>
                        <a href="#" class="mr-4 hover:underline md:mr-6 ">About</a>
                    </li>
                    <li>
                        <a href="#" class="mr-4 hover:underline md:mr-6">Privacy Policy</a>
                    </li>
                    <li>
                        <a href="#" class="mr-4 hover:underline md:mr-6 ">Licensing</a>
                    </li>
                    <li>
                        <a href="#" class="hover:underline">Contact</a>
                    </li>
                </ul>
            </div>
            <hr class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8" />
            <span class="block text-sm text-gray-500 sm:text-center dark:text-gray-400">© 2023 <a
                    href="#!" class="hover:underline">Cookpad</a>. All Rights Reserved.</span>
        </div>
    </footer>
</template>

<style scoped>

</style>