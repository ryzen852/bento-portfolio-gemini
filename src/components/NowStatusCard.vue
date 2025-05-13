<template>
  <div class="card now-status-card">
    <video class="status-background-video" autoplay loop muted playsinline>
      <source :src="videoSource" type="video/mp4"> 
      Your browser does not support the video tag.
    </video>

    
    <div class="card-body status-content"> 
      <div class="d-flex align-items-center mb-2">
        <span class="status-dot me-2"></span>
        <h5 class="card-title mb-0">Now</h5>
      </div>
      <p class="card-text">Currently working at <a class="text-green" href="https://vancouver.ca/" target="_blank">Vancouver</a></p>
    </div>
  </div>
</template>

<script setup>
const videoSource = new URL('../assets/airplane.mp4', import.meta.url).href
</script>

<style scoped>
.now-status-card {
    position: relative;
    overflow: hidden;
    min-height: 150px; /* Keep minimum height as a fallback */
    height: 100%; /* Make the card fill the height of its parent column */
    /* Ensure border-radius is applied correctly with overflow: hidden */
    border-radius: 10px; /* Ensure border-radius matches your card style */
}

.status-background-video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 0;
    filter: brightness(50%);
}

.status-content {
    position: relative;
    z-index: 1;
    color: #f0f0f0;
    /* Adjust padding if needed */
    padding: 1.5rem;
    /* Use flexbox to center content vertically if needed */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start; /* Align items to start (left) */
    height: 100%; /* Make content area fill card height for centering */
}


.status-dot {
  display: inline-block;
  width: 10px;
  height: 10px;
  background-color: #28a745; /* Green color for online status */
  border-radius: 50%;
}

.now-status-card .card-title {
    color: #ffffff;
    margin-bottom: 0.5rem; /* Adjust spacing below title */
}

.now-status-card .card-text {
    
    margin-bottom: 0; /* Remove default paragraph bottom margin */
}


/* Adjust padding if the video covers default card padding */
.now-status-card .card-body {
    padding: 1.5rem; /* Example padding */
}
</style>