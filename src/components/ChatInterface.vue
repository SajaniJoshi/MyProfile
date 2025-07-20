<template>
  <v-card class="chat-card" elevation="8" max-width="400">
    <v-card-title class="text-h6 font-weight-bold text-center pa-4 bg-primary text-white">
      <v-icon class="mr-2">mdi-robot</v-icon>
      Career AI Chat
      <v-btn icon size="small" @click="toggleChat" class="ml-auto">
        <v-icon>{{ isExpanded ? 'mdi-chevron-down' : 'mdi-chevron-up' }}</v-icon>
      </v-btn>
    </v-card-title>
    
    <v-expand-transition>
      <div v-show="isExpanded">
        <v-card-text class="pa-0">
          <!-- Chat Messages -->
          <div class="chat-messages" ref="messagesContainer">
            <div 
              v-for="(message, index) in messages" 
              :key="index"
              :class="['message', message.type]"
            >
              <div class="message-content">
                <v-icon 
                  :icon="message.type === 'user' ? 'mdi-account' : 'mdi-robot'"
                  :color="message.type === 'user' ? 'primary' : 'success'"
                  size="small"
                  class="mr-2"
                ></v-icon>
                <span>{{ message.text }}</span>
              </div>
              <div class="message-time">{{ message.time }}</div>
            </div>
          </div>
        </v-card-text>
        
        <!-- Input Area -->
        <v-card-actions class="pa-4 pt-2">
          <v-text-field
            v-model="newMessage"
            placeholder="Ask about your career..."
            variant="outlined"
            density="compact"
            hide-details
            @keyup.enter="sendMessage"
            class="mr-2"
          ></v-text-field>
          <v-btn
            color="primary"
            icon
            @click="sendMessage"
            :loading="isLoading"
            :disabled="!newMessage.trim()"
          >
            <v-icon>mdi-send</v-icon>
          </v-btn>
        </v-card-actions>
        
        <!-- Alternative Link -->
        <v-divider></v-divider>
        <v-card-actions class="pa-3">
          <v-btn
            color="secondary"
            size="small"
            prepend-icon="mdi-open-in-new"
            @click="openFullChat"
            block
          >
            Open Full AI Chat
          </v-btn>
        </v-card-actions>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script setup lang="ts">
import { ref, nextTick, onMounted } from 'vue'

// Reactive data
const isExpanded = ref(false)
const newMessage = ref('')
const isLoading = ref(false)
const messages = ref([
  {
    type: 'ai',
    text: 'Hello! I\'m your Career AI assistant. How can I help you with your career today?',
    time: new Date().toLocaleTimeString()
  }
])
const messagesContainer = ref(null)

// Methods
const toggleChat = () => {
  isExpanded.value = !isExpanded.value
  if (isExpanded.value) {
    nextTick(() => {
      scrollToBottom()
    })
  }
}

const sendMessage = async () => {
  if (!newMessage.value.trim() || isLoading.value) return
  
  const userMessage = newMessage.value.trim()
  newMessage.value = ''
  
  // Add user message
  messages.value.push({
    type: 'user',
    text: userMessage,
    time: new Date().toLocaleTimeString()
  })
  
  isLoading.value = true
  
  // Simulate AI response (replace with actual API call)
  setTimeout(() => {
    const responses = [
      "That's a great question! Based on your situation, I'd recommend...",
      "I understand your concern. Here are some strategies that might help...",
      "For career development, consider focusing on these areas...",
      "That's an interesting challenge. Let me suggest some approaches...",
      "Based on current industry trends, you might want to consider..."
    ]
    
    const randomResponse = responses[Math.floor(Math.random() * responses.length)]
    
    messages.value.push({
      type: 'ai',
      text: randomResponse,
      time: new Date().toLocaleTimeString()
    })
    
    isLoading.value = false
    nextTick(() => {
      scrollToBottom()
    })
  }, 1000)
}

const scrollToBottom = () => {
  if (messagesContainer.value) {
    messagesContainer.value.scrollTop = messagesContainer.value.scrollHeight
  }
}

const openFullChat = () => {
  window.open('https://SajaniJoshi-career-conversations.hf.space', '_blank')
}

// Lifecycle
onMounted(() => {
  // Auto-expand on mobile
  if (window.innerWidth <= 768) {
    isExpanded.value = true
  }
})
</script>

<style scoped>
.chat-card {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 1000;
  max-height: 500px;
}

.chat-messages {
  height: 300px;
  overflow-y: auto;
  padding: 16px;
  background-color: #f5f5f5;
}

.message {
  margin-bottom: 12px;
  display: flex;
  flex-direction: column;
}

.message.user {
  align-items: flex-end;
}

.message.ai {
  align-items: flex-start;
}

.message-content {
  display: flex;
  align-items: flex-start;
  max-width: 80%;
  padding: 8px 12px;
  border-radius: 12px;
  background-color: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.message.user .message-content {
  background-color: #e3f2fd;
}

.message.ai .message-content {
  background-color: white;
}

.message-time {
  font-size: 0.75rem;
  color: #666;
  margin-top: 4px;
  margin-left: 8px;
}

/* Responsive design */
@media (max-width: 768px) {
  .chat-card {
    bottom: 10px;
    right: 10px;
    left: 10px;
    max-width: none;
  }
  
  .chat-messages {
    height: 250px;
  }
}
</style> 