<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import NavBar from './components/NavBar.vue'
import GradioChatInterface from './components/GradioChatInterface.vue'

// Reactive data
const greeting = ref('Hello!')
const subtitle = ref('Welcome to my portfolio')
const currentTime = ref('')

// Computed property
const welcomeMessage = computed(() => {
  const hour = new Date().getHours()
  if (hour < 12) {
    return 'Good morning!'
  } else if (hour < 18) {
    return 'Good afternoon!'
  } else {
    return 'Good evening!'
  }
})

// Methods
const updateTime = () => {
  currentTime.value = new Date().toLocaleTimeString()
}

// Lifecycle hook
onMounted(() => {
  updateTime()
  // Update time every second
  setInterval(updateTime, 1000)
})
</script>

<template>
  <v-app>
    <NavBar />
    
    <v-main>
      <v-container fluid class="pa-0">
        <!-- Main content area -->
        <div class="text-center pa-8">
          <h1 class="text-h2 font-weight-bold text-dark mb-4">
            {{ greeting }}
          </h1>
          <p class="text-h6 text-grey-darken-1 mb-2">
            {{ welcomeMessage }}
          </p>
          <p class="text-body-1 text-grey-darken-2 mb-6">
            {{ subtitle }}
          </p>
          <p class="text-caption text-grey mb-8">
            Current time: {{ currentTime }}
          </p>
        </div>
      </v-container>
    </v-main>

    <!-- Gradio Chat Interface -->
    <GradioChatInterface />
  </v-app>
</template>

<style>
body {
  font-family: 'Roboto', sans-serif;
}

.v-main {
  background-color: white;
}
</style>
