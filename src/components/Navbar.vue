<script setup lang="ts">
import { ref } from "vue"

const menuOpen = ref(false)
</script>

<template>
  <nav class="fixed top-0 left-0 w-full bg-black/80 backdrop-blur-md text-white shadow-md z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        
        <div class="flex-shrink-0 text-2xl font-bold">
          MyApp
        </div>

        <div class="hidden md:flex space-x-6">
          <a href="#" class="hover:text-gray-300">Home</a>
          <a href="#" class="hover:text-gray-300">About</a>
          <a href="#" class="hover:text-gray-300">Services</a>
          <a href="#" class="hover:text-gray-300">Contact</a>
        </div>

        <div class="md:hidden">
          <button @click="menuOpen = !menuOpen" class="focus:outline-none">
            <svg v-if="!menuOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
              viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16" />
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
              viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <div v-if="menuOpen" class="md:hidden px-4 pb-3 space-y-2 bg-black/90">
      <a href="#" class="block py-2 hover:text-gray-300">Home</a>
      <a href="#" class="block py-2 hover:text-gray-300">About</a>
      <a href="#" class="block py-2 hover:text-gray-300">Services</a>
      <a href="#" class="block py-2 hover:text-gray-300">Contact</a>
    </div>
  </nav>
</template>
