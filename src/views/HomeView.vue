<script setup>
import { ArrowRight, Bell, Calendar, FileText } from 'lucide-vue-next'
import { RouterLink } from 'vue-router'

const announcements = [
  {
    id: 1,
    title: 'Annual General Meeting',
    date: 'May 15, 2026',
    excerpt: 'Join us for the annual general meeting where we will discuss the upcoming community improvements and elect new board members.',
    icon: Calendar
  },
  // {
  //   id: 2,
  //   title: 'Neighborhood Cleanup Drive',
  //   date: 'June 20, 2026',
  //   excerpt: 'Help keep Lumad Apasanon beautiful. Trash bags and gloves will be provided. Breakfast will be served for all volunteers afterwards.',
  //   icon: Bell
  // },
  // {
  //   id: 3,
  //   title: 'New Waste Disposal Guidelines',
  //   date: 'June 5, 2026',
  //   excerpt: 'Please review the updated waste disposal guidelines to ensure our community remains clean and eco-friendly.',
  //   icon: FileText
  // }
]
</script>

<template>
  <div class="flex flex-col">
    <!-- Hero Section -->
    <section class="relative bg-secondary-900 text-white overflow-hidden">
      <div class="absolute inset-0">
        <img 
          src="https://images.unsplash.com/photo-1564013799919-ab600027ffc6?auto=format&fit=crop&q=80&w=2000" 
          alt="Beautiful neighborhood" 
          class="w-full h-full object-cover opacity-30"
        />
        <div class="absolute inset-0 bg-gradient-to-r from-secondary-900 via-secondary-900/80 to-transparent"></div>
      </div>
      
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-24 md:py-32 flex flex-col items-start">
        <span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-primary-500/20 text-primary-200 mb-6 border border-primary-500/30 backdrop-blur-sm">
          Welcome to your community
        </span>
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-extrabold tracking-tight mb-6 max-w-3xl leading-tight">
          Experience the best of <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary-400 to-primary-200">Lumad Apasanon HOA</span>
        </h1>
        <p class="text-lg md:text-xl text-secondary-300 mb-10 max-w-2xl leading-relaxed">
          A vibrant, safe, and welcoming homeowners association dedicated to enhancing the quality of life for all our residents.
        </p>
        <div class="flex flex-col sm:flex-row gap-4">
          <RouterLink to="/portal" class="btn-primary text-lg px-8 py-3">
            Resident Login
          </RouterLink>
          <RouterLink to="/about" class="btn-outline text-lg px-8 py-3 bg-white/10 text-white border-white/20 hover:bg-white/20 hover:border-white/30 backdrop-blur-sm">
            Discover More
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- Announcements Section -->
    <section class="py-20 bg-secondary-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between mb-12">
          <div>
            <h2 class="text-3xl font-bold text-secondary-900 mb-2">Latest Announcements</h2>
            <p class="text-secondary-500">Stay up to date with what's happening in our community.</p>
          </div>
          <RouterLink to="/events" class="hidden sm:inline-flex items-center text-primary-600 hover:text-primary-700 font-medium transition-colors">
            View Calendar
            <ArrowRight class="ml-2 h-4 w-4" />
          </RouterLink>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div 
            v-for="item in announcements" 
            :key="item.id"
            class="bg-white rounded-2xl p-6 shadow-sm border border-secondary-100 hover:shadow-md transition-shadow group cursor-pointer"
          >
            <div class="h-12 w-12 rounded-lg bg-primary-50 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
              <component :is="item.icon" class="h-6 w-6 text-primary-600" />
            </div>
            <div class="text-sm text-primary-600 font-medium mb-2">{{ item.date }}</div>
            <h3 class="text-xl font-bold text-secondary-900 mb-3">{{ item.title }}</h3>
            <p class="text-secondary-500 line-clamp-3 leading-relaxed">{{ item.excerpt }}</p>
          </div>
        </div>
        
        <div class="mt-8 sm:hidden text-center">
          <RouterLink to="/events" class="inline-flex items-center text-primary-600 hover:text-primary-700 font-medium">
            View Calendar
            <ArrowRight class="ml-2 h-4 w-4" />
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- Quick Services -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-3xl font-bold text-secondary-900 mb-16">How can we help you?</h2>
        
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
          <RouterLink to="/documents" class="flex flex-col items-center p-6 rounded-2xl hover:bg-secondary-50 transition-colors group">
            <div class="h-16 w-16 rounded-full bg-secondary-100 flex items-center justify-center mb-4 group-hover:bg-primary-100 transition-colors">
              <FileText class="h-8 w-8 text-secondary-600 group-hover:text-primary-600 transition-colors" />
            </div>
            <h3 class="text-lg font-bold text-secondary-900 mb-2">HOA Documents</h3>
            <p class="text-secondary-500 text-sm">Access bylaws, CC&Rs, and forms.</p>
          </RouterLink>
          
          <RouterLink to="/services" class="flex flex-col items-center p-6 rounded-2xl hover:bg-secondary-50 transition-colors group">
            <div class="h-16 w-16 rounded-full bg-secondary-100 flex items-center justify-center mb-4 group-hover:bg-primary-100 transition-colors">
              <Bell class="h-8 w-8 text-secondary-600 group-hover:text-primary-600 transition-colors" />
            </div>
            <h3 class="text-lg font-bold text-secondary-900 mb-2">Report a Concern</h3>
            <p class="text-secondary-500 text-sm">Submit maintenance requests.</p>
          </RouterLink>
          
          <RouterLink to="/events" class="flex flex-col items-center p-6 rounded-2xl hover:bg-secondary-50 transition-colors group">
            <div class="h-16 w-16 rounded-full bg-secondary-100 flex items-center justify-center mb-4 group-hover:bg-primary-100 transition-colors">
              <Calendar class="h-8 w-8 text-secondary-600 group-hover:text-primary-600 transition-colors" />
            </div>
            <h3 class="text-lg font-bold text-secondary-900 mb-2">Community Events</h3>
            <p class="text-secondary-500 text-sm">See upcoming meetings and activities.</p>
          </RouterLink>
          
          <RouterLink to="/portal" class="flex flex-col items-center p-6 rounded-2xl hover:bg-secondary-50 transition-colors group">
            <div class="h-16 w-16 rounded-full bg-secondary-100 flex items-center justify-center mb-4 group-hover:bg-primary-100 transition-colors">
              <Home class="h-8 w-8 text-secondary-600 group-hover:text-primary-600 transition-colors" />
            </div>
            <h3 class="text-lg font-bold text-secondary-900 mb-2">Resident Portal</h3>
            <p class="text-secondary-500 text-sm">Manage your account and payments.</p>
          </RouterLink>
        </div>
      </div>
    </section>
  </div>
</template>
