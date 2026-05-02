<script setup>
import { MapPin, Phone, Mail, Home } from 'lucide-vue-next'
</script>

<template>
  <footer class="bg-secondary-900 text-white pt-12 pb-8">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-8">
        <div>
          <div class="flex items-center gap-2 mb-4">
            <Home class="h-6 w-6 text-primary-400" />
            <span class="font-bold text-xl tracking-tight">Lumad Apasanon</span>
          </div>
          <p class="text-secondary-400 text-sm leading-relaxed mb-6">
            Dedicated to maintaining a beautiful, safe, and welcoming community for all our residents.
          </p>
        </div>
        
        <div>
          <h3 class="text-sm font-semibold uppercase tracking-wider mb-4 text-secondary-300">Quick Links</h3>
          <ul class="space-y-2">
            <li><RouterLink to="/about" class="text-secondary-400 hover:text-white transition-colors">About Us</RouterLink></li>
            <li><RouterLink to="/documents" class="text-secondary-400 hover:text-white transition-colors">Documents</RouterLink></li>
            <li><RouterLink to="/events" class="text-secondary-400 hover:text-white transition-colors">Events Calendar</RouterLink></li>
            <li><RouterLink to="/services" class="text-secondary-400 hover:text-white transition-colors">Submit a Concern</RouterLink></li>
          </ul>
        </div>

        <div>
          <h3 class="text-sm font-semibold uppercase tracking-wider mb-4 text-secondary-300">Contact Us</h3>
          <ul class="space-y-3">
            <li class="flex items-start text-secondary-400">
              <MapPin class="h-5 w-5 mr-2 text-primary-400 shrink-0" />
              <span>Sitio Central Apas, Barangay Apas, <br/> Cebu City, Philippines 6000</span>
            </li>
            <li class="flex items-center text-secondary-400">
              <Phone class="h-5 w-5 mr-2 text-primary-400 shrink-0" />
              <span>(032) 123-4567</span>
            </li>
            <li class="flex items-center text-secondary-400">
              <Mail class="h-5 w-5 mr-2 text-primary-400 shrink-0" />
              <span>board@lumadapasanon.org</span>
            </li>
          </ul>
        </div>
      </div>
      
      <div class="border-t border-secondary-800 pt-8 flex flex-col md:flex-row justify-between items-center text-sm text-secondary-500">
        <p>&copy; {{ new Date().getFullYear() }} Lumad Apasanon HOA. All rights reserved.</p>
        <div class="mt-4 md:mt-0 flex space-x-4">
          <RouterLink to="/portal" class="hover:text-white transition-colors">Resident Portal</RouterLink>
          <span>|</span>
          <a href="#" class="hover:text-white transition-colors">Privacy Policy</a>
        </div>
      </div>
    </div>
  </footer>
</template>
