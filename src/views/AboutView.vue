<script setup>
const placeholderImg = 'https://placehold.co/256x256/f1f5f9/94a3b8?text=Photo'

const president = {
  name: 'Scott A. Cabigon',
  role: 'Acting President',
  image: '/images/scott.png',
  bio: 'Leading the interim board to ensure smooth operations and community welfare.'
}

const boardMembers = [
  {
    name: 'Jocelyn V. Puyod',
    role: 'Interim Board of Directors',
    image: '/images/jocelyn.png',
    bio: ''
  },
  {
    name: 'Josephine A. Lagura',
    role: 'Interim Board of Directors',
    image: '/images/josephine.png',
    bio: ''
  },
  {
    name: 'Emilda L. Salingujay',
    role: 'Interim Board of Directors',
    image: placeholderImg,
    bio: ''
  },
  {
    name: 'Philip R. Alkuino',
    role: 'Interim Board of Directors',
    image: placeholderImg,
    bio: ''
  }
]
</script>

<template>
  <div class="py-16 sm:py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Overview Section -->
      <div class="text-center max-w-3xl mx-auto mb-20">
        <h1 class="text-4xl font-extrabold text-secondary-900 tracking-tight mb-4">About Lumad Apasanon</h1>
        <p class="text-xl text-secondary-500 leading-relaxed">
          Founded in 2025, Lumad Apasanon is a vibrant residential community located in the heart of Apas, Cebu City. 
          We pride ourselves on fostering a safe, inclusive, and beautiful environment for all our families.
        </p>
      </div>

      <!-- Vision & Mission -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 mb-24">
        <div class="bg-primary-50 rounded-3xl p-10">
          <h2 class="text-2xl font-bold text-primary-900 mb-4">Our Vision</h2>
          <p class="text-primary-700 leading-relaxed">
            To be the premier residential community in Cebu, recognized for our harmonious neighborhood, 
            well-maintained amenities, and active resident participation.
          </p>
        </div>
        <div class="bg-secondary-100 rounded-3xl p-10">
          <h2 class="text-2xl font-bold text-secondary-900 mb-4">Our Mission</h2>
          <p class="text-secondary-700 leading-relaxed">
            To enhance the quality of life and property values of our residents by providing efficient 
            management of common areas, enforcing community rules fairly, and organizing engaging activities.
          </p>
        </div>
      </div>

      <!-- Board Members -->
      <div>
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-secondary-900">Interim Board of Directors</h2>
          <p class="mt-4 text-lg text-secondary-500">The dedicated team serving our community.</p>
        </div>
        
        <!-- Acting President (Centered) -->
        <div class="flex justify-center mb-12">
          <div class="bg-white rounded-2xl p-6 shadow-sm border border-secondary-100 text-center max-w-sm w-full">
            <img class="w-40 h-40 rounded-full mx-auto mb-4 object-cover ring-4 ring-primary-50" :src="president.image" :alt="president.name" />
            <h3 class="text-2xl font-bold text-secondary-900">{{ president.name }}</h3>
            <p class="text-primary-600 font-medium text-base mb-4">{{ president.role }}</p>
            <p v-if="president.bio" class="text-secondary-500 text-sm leading-relaxed">{{ president.bio }}</p>
          </div>
        </div>

        <!-- Other Board Members -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="member in boardMembers" :key="member.name" class="bg-white rounded-2xl p-6 shadow-sm border border-secondary-100 text-center">
            <img class="w-32 h-32 rounded-full mx-auto mb-4 object-cover ring-4 ring-primary-50" :src="member.image" :alt="member.name" />
            <h3 class="text-xl font-bold text-secondary-900">{{ member.name }}</h3>
            <p class="text-primary-600 font-medium text-sm mb-4">{{ member.role }}</p>
            <p v-if="member.bio" class="text-secondary-500 text-sm leading-relaxed">{{ member.bio }}</p>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>
