<template>
  <v-app-bar app elevation="0" color="white">
    <v-container class="d-flex align-center justify-space-between">
      <!-- Left side - Navigation links -->
      <div class="d-flex align-center">
        <v-btn 
          text 
          :color="activeSection === 'work' ? 'primary' : 'dark'" 
          class="text-none font-weight-bold mr-4"
          @click="setActiveSection('work')"
        >
          work
        </v-btn>
        <v-btn 
          text 
          :color="activeSection === 'about' ? 'primary' : 'grey'" 
          class="text-none"
          @click="setActiveSection('about')"
        >
          about / contact
        </v-btn>
      </div>

      <!-- Center - Name -->
      <div class="text-center">
        <h1 class="text-h5 font-weight-bold text-dark">
          {{ fullName }}
        </h1>
      </div>

      <!-- Right side - Social media links -->
      <div class="d-flex align-center">
        <v-btn 
          v-for="social in socialLinks" 
          :key="social.name"
          icon 
          color="dark" 
          class="mr-2" 
          :href="social.url" 
          target="_blank"
          :title="social.name"
        >
          <v-icon>{{ social.icon }}</v-icon>
        </v-btn>
      </div>
    </v-container>
  </v-app-bar>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

// Reactive data
const activeSection = ref('work')
const firstName = ref('Sajani')
const lastName = ref('Joshi')

// Computed property
const fullName = computed(() => `${firstName.value} ${lastName.value}`)

// Reactive array
const socialLinks = ref([
  {
    name: 'LinkedIn',
    url: 'https://linkedin.com',
    icon: 'mdi-linkedin'
  },
  {
    name: 'Instagram',
    url: 'https://instagram.com',
    icon: 'mdi-instagram'
  },
  {
    name: 'Facebook',
    url: 'https://facebook.com',
    icon: 'mdi-facebook'
  }
])

// Methods
const setActiveSection = (section: string) => {
  activeSection.value = section
  console.log(`Active section changed to: ${section}`)
}
</script>

<style scoped>
.v-app-bar {
  border-bottom: 1px solid #e0e0e0;
}
</style> 