<template>
  <div class="bg-gray-100 h-full">
    <Navbar />
    <main class="">
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Navbar from './Navbar.vue';
import Footer from './Footer.vue'; 
</script>
