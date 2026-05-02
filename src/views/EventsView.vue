<script setup>
import { Calendar as CalendarIcon, MapPin, Clock } from 'lucide-vue-next'

const events = [
  {
    id: 1,
    title: 'Annual General Meeting',
    date: 'May 08, 2026',
    time: '6:00 PM - 8:00 PM',
    location: 'Sitio Central Apas, Barangay Apas Gym',
    description: 'Join us for the general meeting. We will discuss upcoming community improvements and elect new board members. Attendance is highly encouraged.',
    type: 'Meeting'
  },
  // {
  //   id: 2,
  //   title: 'Neighborhood Cleanup Drive',
  //   date: 'June 20, 2026',
  //   time: '8:00 AM - 11:00 AM',
  //   location: 'Main Park',
  //   description: 'Help keep Lumad Apasanon beautiful. Trash bags and gloves will be provided. Breakfast will be served for all volunteers afterwards.',
  //   type: 'Volunteer'
  // },
  // {
  //   id: 3,
  //   title: 'New Waste Disposal Guidelines',
  //   date: 'June 5, 2026',
  //   time: '10:00 AM - 3:00 PM',
  //   location: 'Barangay Gym',
  //   description: 'Please review the updated waste disposal guidelines to ensure our community remains clean and eco-friendly.',
  //   type: 'Volunteer'
  // },
  
]
</script>

<template>
  <div class="py-16 sm:py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <div class="mb-12">
        <h1 class="text-4xl font-extrabold text-secondary-900 tracking-tight mb-4">Events & Calendar</h1>
        <p class="text-xl text-secondary-500 max-w-3xl">
          Stay connected with your community. Check out our upcoming meetings, social events, and volunteer opportunities.
        </p>
      </div>

      <div class="space-y-8">
        <div v-for="event in events" :key="event.id" class="bg-white rounded-2xl shadow-sm border border-secondary-100 overflow-hidden flex flex-col md:flex-row hover:shadow-md transition-shadow">
          
          <!-- Date Column -->
          <div class="bg-primary-50 p-6 md:w-64 flex flex-col justify-center items-center text-center border-b md:border-b-0 md:border-r border-secondary-100 shrink-0">
            <CalendarIcon class="h-8 w-8 text-primary-600 mb-2" />
            <div class="text-2xl font-bold text-primary-900">{{ event.date.split(' ')[0] }} {{ event.date.split(' ')[1].replace(',', '') }}</div>
            <div class="text-primary-600 font-medium">{{ event.date.split(' ')[2] }}</div>
            <span class="mt-4 inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-white text-primary-700 border border-primary-200">
              {{ event.type }}
            </span>
          </div>

          <!-- Details Column -->
          <div class="p-6 md:p-8 flex-1">
            <h2 class="text-2xl font-bold text-secondary-900 mb-4">{{ event.title }}</h2>
            
            <div class="flex flex-col sm:flex-row sm:items-center gap-4 text-sm text-secondary-600 mb-6">
              <div class="flex items-center">
                <Clock class="h-4 w-4 mr-2 text-secondary-400" />
                {{ event.time }}
              </div>
              <div class="hidden sm:block text-secondary-300">•</div>
              <div class="flex items-center">
                <MapPin class="h-4 w-4 mr-2 text-secondary-400" />
                {{ event.location }}
              </div>
            </div>

            <p class="text-secondary-600 leading-relaxed mb-6">
              {{ event.description }}
            </p>

            <button class="btn-outline text-sm">Add to Calendar</button>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>
