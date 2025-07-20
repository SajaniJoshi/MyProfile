<template>
  <div class="gradio-chat-container">
    <!-- Gradio chatbot iframe -->
    <iframe
      src="https://SajaniJoshi-career-conversations.hf.space"
      class="chatbot-frame"
      frameborder="0"
      title="Career AI Chat"
    ></iframe>
  </div>
</template>

<script setup lang="ts">
// No additional logic needed for direct iframe embed
</script>

<style scoped>
.gradio-chat-container {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 1000;
  width: 400px;
  height: 500px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
  background-color: white;
}

.chatbot-frame {
  width: 100%;
  height: 100%;
  border: none;
  border-radius: 12px;
  background-color: white;
}

/* Responsive design for mobile */
@media (max-width: 768px) {
  .gradio-chat-container {
    bottom: 10px;
    right: 10px;
    left: 10px;
    width: auto;
    height: 400px;
  }
}
</style> 