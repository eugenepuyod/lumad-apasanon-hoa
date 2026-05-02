<script setup>
import { Download, FileText, FileSearch } from 'lucide-vue-next'

const documentCategories = [
  {
    title: 'Governing Documents',
    description: 'The foundational rules and regulations of our community.',
    icon: FileSearch,
    files: [
      { name: 'APPOINTMENT OF INTERIM BOARD OF DIRECTORS', size: '2.1 MB', date: 'Jan 2010' },
      // { name: 'Bylaws', size: '4.5 MB', date: 'Mar 2015' },
      // { name: 'CC&Rs (Covenants, Conditions, and Restrictions)', size: '6.8 MB', date: 'Mar 2015' },
    ]
  },
  {
    title: 'Meeting Minutes',
    description: 'Records of our monthly board meetings and annual general meetings.',
    icon: FileText,
    files: [
      { name: 'Board Meeting Minutes - April 2026', size: '1.2 MB', date: 'Apr 2026' },
      // { name: 'Board Meeting Minutes - March 2026', size: '1.1 MB', date: 'Mar 2026' },
      // { name: 'Annual General Meeting 2025', size: '3.4 MB', date: 'Dec 2025' },
    ]
  },
  {
    title: 'Forms & Applications',
    description: 'Downloadable forms for various requests and registrations.',
    icon: Download,
    files: [
      { name: 'Architectural Modification Request', size: '0.8 MB', date: 'Jan 2026' },
      // { name: 'Clubhouse Reservation Form', size: '0.5 MB', date: 'Feb 2026' },
      // { name: 'Vehicle Registration Form', size: '0.6 MB', date: 'Jan 2026' },
    ]
  }
]

const handleDownload = (fileName) => {
  // Create a dummy text blob for demonstration since real PDFs aren't available
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
      
      <div class="mb-12">
        <h1 class="text-4xl font-extrabold text-secondary-900 tracking-tight mb-4">Community Documents</h1>
        <p class="text-xl text-secondary-500 max-w-3xl">
          Access important HOA documents, meeting minutes, and forms. 
          For private documents related to your specific unit, please log in to the Resident Portal.
        </p>
      </div>

      <div class="space-y-12">
        <div v-for="category in documentCategories" :key="category.title" class="bg-white rounded-3xl shadow-sm border border-secondary-100 overflow-hidden">
          <div class="p-8 md:p-10 border-b border-secondary-100 bg-secondary-50/50">
            <div class="flex items-center gap-4 mb-2">
              <div class="bg-primary-100 p-3 rounded-xl">
                <component :is="category.icon" class="h-6 w-6 text-primary-600" />
              </div>
              <h2 class="text-2xl font-bold text-secondary-900">{{ category.title }}</h2>
            </div>
            <p class="text-secondary-500 ml-16">{{ category.description }}</p>
          </div>
          
          <ul class="divide-y divide-secondary-100">
            <li v-for="file in category.files" :key="file.name" class="p-6 md:px-10 flex flex-col sm:flex-row sm:items-center justify-between hover:bg-secondary-50 transition-colors group">
              <div class="flex items-start gap-4 mb-4 sm:mb-0">
                <FileText class="h-6 w-6 text-secondary-400 mt-1" />
                <div>
                  <h3 class="text-lg font-medium text-secondary-900 group-hover:text-primary-600 transition-colors">{{ file.name }}</h3>
                  <p class="text-sm text-secondary-500">PDF Document • {{ file.size }} • Updated {{ file.date }}</p>
                </div>
              </div>
              <button @click="handleDownload(file.name)" class="btn-outline sm:w-auto w-full group-hover:border-primary-500 group-hover:text-primary-600">
                <Download class="h-4 w-4 mr-2" />
                Download
              </button>
            </li>
          </ul>
        </div>
      </div>

    </div>
  </div>
</template>
