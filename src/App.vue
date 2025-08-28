<script setup lang="ts">
import ParticlesBg from '@/components/ui/particles-bg/ParticlesBg.vue'
import { computed, ref } from "vue"
import { useColorMode } from "@vueuse/core"
import { Sun, Moon, ChevronDown, Menu, X } from "lucide-vue-next" // tambah Menu & X icon

const colorMode = useColorMode()
const isDark = computed(() => colorMode.value === "dark")
const toggleDark = () => {
  colorMode.value = isDark.value ? "light" : "dark"
}

const menuOpen = ref(false)
</script>

<template>
  <div class="relative h-screen w-screen overflow-hidden bg-background">
    <ParticlesBg
      class="absolute inset-0"
      :quantity="120"
      :ease="100"
      :color="isDark ? '#FFF' : '#000'"
      :staticity="10"
      refresh
    />

    <nav class="fixed top-4 left-1/2 -translate-x-1/2 z-50 w-[90%] max-w-5xl">
      <div
        class="flex items-center justify-between px-6 py-3 bg-neutral-900/90 text-white 
               rounded-2xl shadow-lg border border-neutral-800 backdrop-blur-md"
      >
        <div class="flex items-center gap-2 font-bold text-lg">
          <div class="bg-orange-600 p-2 rounded-md">
            <ChevronDown class="w-4 h-4" />
          </div>
          <span>DEMO</span>
        </div>

        <div class="hidden md:flex items-center gap-6 ml-10 font-medium">
          <div class="flex items-center gap-1 cursor-pointer hover:text-orange-400">
            Features
            <ChevronDown class="w-4 h-4" />
          </div>
          <a href="#" class="hover:text-orange-400">Dokumentasi</a>
          <a href="#" class="hover:text-orange-400">Team</a>
          <a href="#" class="hover:text-orange-400">Kontak</a>
          <a href="#" class="hover:text-orange-400">FAQ</a>
        </div>

        <div class="flex items-center gap-2">
          <button
            @click="toggleDark"
            class="p-2 rounded-full hover:bg-neutral-700 transition"
          >
            <Sun v-if="!isDark" class="w-5 h-5" />
            <Moon v-else class="w-5 h-5" />
          </button>

          <button
            @click="menuOpen = !menuOpen"
            class="md:hidden p-2 rounded-full hover:bg-neutral-700 transition"
          >
            <Menu v-if="!menuOpen" class="w-6 h-6" />
            <X v-else class="w-6 h-6" />
          </button>
        </div>
      </div>

      <transition name="fade">
        <div
          v-if="menuOpen"
          class="mt-2 flex flex-col gap-3 bg-neutral-900/95 text-white rounded-xl shadow-lg border border-neutral-800 p-4 md:hidden"
        >
          <a href="#" class="hover:text-orange-400">Features</a>
          <a href="#" class="hover:text-orange-400">Dokumentasi</a>
          <a href="#" class="hover:text-orange-400">Team</a>
          <a href="#" class="hover:text-orange-400">Kontak</a>
          <a href="#" class="hover:text-orange-400">FAQ</a>
        </div>
      </transition>
    </nav>

    <div class="relative z-10 flex h-full items-center justify-center">
      <h1 class="text-5xl font-bold text-white drop-shadow-lg">
        DEMO
      </h1>
    </div>
  </div>
</template>

<style>
.fade-enter-active, .fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
