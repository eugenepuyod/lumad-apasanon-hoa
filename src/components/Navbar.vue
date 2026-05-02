<script setup>
import { ref } from 'vue'
import { RouterLink, useRoute } from 'vue-router'
import { Menu, X, Home } from 'lucide-vue-next'

const route = useRoute()
const isMenuOpen = ref(false)

const navLinks = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Documents', path: '/documents' },
  { name: 'Events', path: '/events' },
  { name: 'Services', path: '/services' },
]

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}
</script>

<template>
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">
        <div class="flex items-center">
          <RouterLink to="/" class="flex-shrink-0 flex items-center gap-2 group">
            <div class="bg-primary-600 p-2 rounded-lg group-hover:bg-primary-700 transition-colors">
              <Home class="h-6 w-6 text-white" />
            </div>
            <span class="font-bold text-xl text-secondary-900 tracking-tight">Lumad Apasanon</span>
          </RouterLink>
        </div>
        
        <!-- Desktop menu -->
        <div class="hidden sm:flex sm:items-center sm:space-x-8">
          <RouterLink 
            v-for="link in navLinks" 
            :key="link.path"
            :to="link.path"
            class="inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium transition-colors"
            :class="[
              route.path === link.path 
                ? 'border-primary-500 text-secondary-900' 
                : 'border-transparent text-secondary-500 hover:border-secondary-300 hover:text-secondary-700'
            ]"
          >
            {{ link.name }}
          </RouterLink>
          <RouterLink to="/portal" class="btn-primary ml-4">
            Resident Portal
          </RouterLink>
        </div>

        <!-- Mobile menu button -->
        <div class="flex items-center sm:hidden">
          <button 
            @click="toggleMenu"
            type="button" 
            class="inline-flex items-center justify-center p-2 rounded-md text-secondary-400 hover:text-secondary-500 hover:bg-secondary-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-primary-500"
            aria-expanded="false"
          >
            <span class="sr-only">Open main menu</span>
            <Menu v-if="!isMenuOpen" class="block h-6 w-6" aria-hidden="true" />
            <X v-else class="block h-6 w-6" aria-hidden="true" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile menu, show/hide based on menu state. -->
    <div v-show="isMenuOpen" class="sm:hidden border-t border-secondary-200 bg-white">
      <div class="pt-2 pb-3 space-y-1">
        <RouterLink 
          v-for="link in navLinks" 
          :key="link.path"
          :to="link.path"
          @click="isMenuOpen = false"
          class="block pl-3 pr-4 py-2 border-l-4 text-base font-medium"
          :class="[
            route.path === link.path
              ? 'bg-primary-50 border-primary-500 text-primary-700'
              : 'border-transparent text-secondary-500 hover:bg-secondary-50 hover:border-secondary-300 hover:text-secondary-700'
          ]"
        >
          {{ link.name }}
        </RouterLink>
        <div class="px-4 py-3">
          <RouterLink to="/portal" @click="isMenuOpen = false" class="btn-primary w-full justify-center">
            Resident Portal
          </RouterLink>
        </div>
      </div>
    </div>
  </nav>
</template>
