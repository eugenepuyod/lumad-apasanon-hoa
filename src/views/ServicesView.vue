<script setup>
import { ref } from 'vue'
import { Send, CheckCircle } from 'lucide-vue-next'

const isSubmitted = ref(false)
const formData = ref({
  name: '',
  unit: '',
  subject: '',
  description: '',
  type: 'maintenance'
})

const submitForm = () => {
  // Mock submission
  console.log('Submitting concern:', formData.value)
  isSubmitted.value = true
  
  // Reset after 3 seconds for demo purposes
  setTimeout(() => {
    isSubmitted.value = false
    formData.value = {
      name: '',
      unit: '',
      subject: '',
      description: '',
      type: 'maintenance'
    }
  }, 5000)
}
</script>

<template>
  <div class="bg-secondary-50 min-h-screen py-16 sm:py-24">
    <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <div class="text-center mb-12">
        <h1 class="text-4xl font-extrabold text-secondary-900 tracking-tight mb-4">Resident Services</h1>
        <p class="text-xl text-secondary-500">
          Submit a maintenance request, report a concern, or contact the HOA board directly.
        </p>
      </div>

      <div class="bg-white rounded-3xl shadow-sm border border-secondary-100 p-8 sm:p-12 relative overflow-hidden">
        
        <!-- Success State Overlay -->
        <div v-if="isSubmitted" class="absolute inset-0 bg-white/95 backdrop-blur-sm z-10 flex flex-col items-center justify-center p-8 text-center transition-all">
          <div class="h-20 w-20 bg-green-100 rounded-full flex items-center justify-center mb-6">
            <CheckCircle class="h-10 w-10 text-green-600" />
          </div>
          <h2 class="text-2xl font-bold text-secondary-900 mb-2">Request Submitted!</h2>
          <p class="text-secondary-500 max-w-md">
            Thank you for reaching out. The HOA board has received your concern and will get back to you within 2-3 business days.
          </p>
        </div>

        <form @submit.prevent="submitForm" class="space-y-6">
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
            <div>
              <label for="name" class="block text-sm font-medium text-secondary-700 mb-2">Full Name</label>
              <input type="text" id="name" v-model="formData.name" required class="w-full px-4 py-3 rounded-xl border border-secondary-300 focus:ring-2 focus:ring-primary-500 focus:border-primary-500 transition-shadow">
            </div>
            <div>
              <label for="unit" class="block text-sm font-medium text-secondary-700 mb-2">Unit / Lot Number</label>
              <input type="text" id="unit" v-model="formData.unit" required class="w-full px-4 py-3 rounded-xl border border-secondary-300 focus:ring-2 focus:ring-primary-500 focus:border-primary-500 transition-shadow">
            </div>
          </div>

          <div>
            <label for="type" class="block text-sm font-medium text-secondary-700 mb-2">Request Type</label>
            <select id="type" v-model="formData.type" class="w-full px-4 py-3 rounded-xl border border-secondary-300 focus:ring-2 focus:ring-primary-500 focus:border-primary-500 transition-shadow bg-white">
              <option value="maintenance">Maintenance Request</option>
              <option value="complaint">Noise/Rule Violation Complaint</option>
              <option value="suggestion">Community Suggestion</option>
              <option value="other">Other Inquiry</option>
            </select>
          </div>

          <div>
            <label for="subject" class="block text-sm font-medium text-secondary-700 mb-2">Subject</label>
            <input type="text" id="subject" v-model="formData.subject" required class="w-full px-4 py-3 rounded-xl border border-secondary-300 focus:ring-2 focus:ring-primary-500 focus:border-primary-500 transition-shadow">
          </div>

          <div>
            <label for="description" class="block text-sm font-medium text-secondary-700 mb-2">Description</label>
            <textarea id="description" v-model="formData.description" rows="5" required class="w-full px-4 py-3 rounded-xl border border-secondary-300 focus:ring-2 focus:ring-primary-500 focus:border-primary-500 transition-shadow resize-none placeholder-secondary-400" placeholder="Please provide as much detail as possible..."></textarea>
          </div>

          <div class="pt-4">
            <button type="submit" class="btn-primary w-full py-3 text-lg justify-center group">
              Submit Request
              <Send class="ml-2 h-5 w-5 group-hover:translate-x-1 transition-transform" />
            </button>
          </div>
        </form>
      </div>

    </div>
  </div>
</template>
