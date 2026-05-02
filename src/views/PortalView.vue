<script setup>
import { ref } from 'vue'
import { User, Lock, CreditCard, FileText, Settings, LogOut } from 'lucide-vue-next'

const isLoggedIn = ref(false)
const loginForm = ref({
  email: '',
  password: ''
})

const handleLogin = () => {
  // Mock login: any credentials work for demo purposes
  if (loginForm.value.email && loginForm.value.password) {
    isLoggedIn.value = true
  }
}

const handleLogout = () => {
  isLoggedIn.value = false
  loginForm.value = { email: '', password: '' }
}

const userAccount = {
  name: 'Juan Dela Cruz',
  unit: 'Lot 15, Block 3',
  status: 'Good Standing',
  balance: '₱ 0.00',
  nextDue: 'June 1, 2026'
}

const privateDocuments = [
  { name: 'Monthly Statement - April 2026', type: 'PDF' },
  { name: 'Violation Notice - None', type: 'System' },
  { name: 'Vehicle Registration Card', type: 'PDF' }
]

const handleDownload = (fileName) => {
  const content = `This is a placeholder document for: ${fileName}\n\nIn a fully integrated backend, this would download the actual PDF file.`
  const blob = new Blob([content], { type: 'text/plain' })
  const url = URL.createObjectURL(blob)
  
  const a = document.createElement('a')
  a.href = url
  a.download = `${fileName.replace(/\s+/g, '_')}.txt`
  document.body.appendChild(a)
  a.click()
  document.body.removeChild(a)
  URL.revokeObjectURL(url)
}
</script>

<template>
  <div class="bg-secondary-50 min-h-screen py-16 sm:py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Login View -->
      <div v-if="!isLoggedIn" class="max-w-md mx-auto bg-white rounded-3xl shadow-sm border border-secondary-100 p-8 sm:p-10">
        <div class="text-center mb-8">
          <div class="h-16 w-16 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-4">
            <Lock class="h-8 w-8 text-primary-600" />
          </div>
          <h1 class="text-3xl font-extrabold text-secondary-900 tracking-tight">Resident Portal</h1>
          <p class="mt-2 text-secondary-500 text-sm">Sign in to access your private account</p>
        </div>

        <form @submit.prevent="handleLogin" class="space-y-6">
          <div>
            <label for="email" class="block text-sm font-medium text-secondary-700 mb-2">Email Address</label>
            <div class="relative">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <User class="h-5 w-5 text-secondary-400" />
              </div>
              <input type="email" id="email" v-model="loginForm.email" required class="block w-full pl-10 pr-3 py-3 border border-secondary-300 rounded-xl focus:ring-primary-500 focus:border-primary-500 transition-shadow">
            </div>
          </div>
          
          <div>
            <label for="password" class="block text-sm font-medium text-secondary-700 mb-2">Password</label>
            <div class="relative">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <Lock class="h-5 w-5 text-secondary-400" />
              </div>
              <input type="password" id="password" v-model="loginForm.password" required class="block w-full pl-10 pr-3 py-3 border border-secondary-300 rounded-xl focus:ring-primary-500 focus:border-primary-500 transition-shadow">
            </div>
          </div>

          <div class="flex items-center justify-between text-sm">
            <label class="flex items-center">
              <input type="checkbox" class="rounded border-secondary-300 text-primary-600 focus:ring-primary-500 h-4 w-4">
              <span class="ml-2 text-secondary-600">Remember me</span>
            </label>
            <a href="#" class="text-primary-600 hover:text-primary-500 font-medium">Forgot password?</a>
          </div>

          <button type="submit" class="btn-primary w-full py-3 justify-center text-lg">
            Sign In
          </button>
        </form>
        
        <!-- Note for demo -->
        <p class="mt-6 text-xs text-center text-secondary-400">
          Demo: Enter any email and password to log in.
        </p>
      </div>

      <!-- Authenticated Dashboard -->
      <div v-else>
        <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-8 gap-4">
          <div>
            <h1 class="text-3xl font-extrabold text-secondary-900 tracking-tight">Welcome, {{ userAccount.name }}</h1>
            <p class="text-secondary-500">{{ userAccount.unit }}</p>
          </div>
          <button @click="handleLogout" class="btn-outline">
            <LogOut class="h-4 w-4 mr-2" />
            Sign Out
          </button>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
          
          <!-- Account Summary -->
          <div class="lg:col-span-1 space-y-8">
            <div class="bg-white rounded-3xl shadow-sm border border-secondary-100 p-8">
              <h2 class="text-lg font-bold text-secondary-900 mb-6 flex items-center">
                <CreditCard class="h-5 w-5 mr-2 text-primary-500" />
                Account Balance
              </h2>
              <div class="text-4xl font-extrabold text-secondary-900 mb-2">{{ userAccount.balance }}</div>
              <p class="text-sm text-secondary-500 mb-6">Next payment due: {{ userAccount.nextDue }}</p>
              <button class="btn-primary w-full justify-center">Make a Payment</button>
            </div>

            <div class="bg-white rounded-3xl shadow-sm border border-secondary-100 p-8">
              <h2 class="text-lg font-bold text-secondary-900 mb-6 flex items-center">
                <Settings class="h-5 w-5 mr-2 text-primary-500" />
                Account Status
              </h2>
              <div class="flex items-center justify-between py-3 border-b border-secondary-100">
                <span class="text-secondary-600 text-sm">Status</span>
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800">
                  {{ userAccount.status }}
                </span>
              </div>
              <div class="flex items-center justify-between py-3">
                <span class="text-secondary-600 text-sm">Gate Pass</span>
                <span class="text-sm font-medium text-secondary-900">Active</span>
              </div>
            </div>
          </div>

          <!-- Private Documents & Activity -->
          <div class="lg:col-span-2 space-y-8">
            <div class="bg-white rounded-3xl shadow-sm border border-secondary-100 p-8">
              <div class="flex justify-between items-center mb-6">
                <h2 class="text-lg font-bold text-secondary-900 flex items-center">
                  <FileText class="h-5 w-5 mr-2 text-primary-500" />
                  My Private Documents
                </h2>
                <button class="text-sm text-primary-600 hover:text-primary-700 font-medium">View All</button>
              </div>
              
              <ul class="divide-y divide-secondary-100">
                <li v-for="(doc, idx) in privateDocuments" :key="idx" class="py-4 flex items-center justify-between group">
                  <div class="flex items-center">
                    <div class="h-10 w-10 rounded-lg bg-secondary-50 flex items-center justify-center mr-4">
                      <FileText class="h-5 w-5 text-secondary-400" />
                    </div>
                    <div>
                      <p class="text-sm font-medium text-secondary-900 group-hover:text-primary-600 transition-colors">{{ doc.name }}</p>
                      <p class="text-xs text-secondary-500">{{ doc.type }}</p>
                    </div>
                  </div>
                  <button @click="handleDownload(doc.name)" class="text-secondary-400 hover:text-primary-600 p-2">
                    <span class="sr-only">Download</span>
                    <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
                    </svg>
                  </button>
                </li>
              </ul>
            </div>
          </div>

        </div>
      </div>

    </div>
  </div>
</template>
