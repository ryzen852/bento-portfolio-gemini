<template>
  <div class="card">
    <div class="card-body d-flex flex-column justify-content-center align-items-center">
      <h5 class="card-title mb-3 text-green">Time Zone</h5>
      <p class="display-6 mb-0">{{ currentTime }}</p>
       <p class="card-text text-muted">{{ timeZoneName }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const currentTime = ref('');
const timeZoneName = ref('');
let timer;

const updateTime = () => {
  const now = new Date();
  currentTime.value = now.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false });
  timeZoneName.value = Intl.DateTimeFormat().resolvedOptions().timeZone;
};

onMounted(() => {
  updateTime();
  timer = setInterval(updateTime, 1000); // Update every second
});

onUnmounted(() => {
  clearInterval(timer);
});
</script>

<style scoped>
/* Adjust font size for time display */
.display-6 {
    font-size: 2.5rem;
}
</style>