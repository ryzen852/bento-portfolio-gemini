<template>
  <div class="custom-dark-theme">
    <div class="container-fluid py-4">
      <div class="row g-4 m-4">
        <div class="col-12 col-md-3 col-lg-3 animate-on-load fade-in-right" style="animation-delay: 0.1s;">
          <NowStatusCard />
        </div>
        <div class="col-12 col-md-9 col-lg-9 animate-on-load fade-in-left" style="animation-delay: 0.2s;">
          <IntroCard />
        </div>

        <div class="col-12 col-md-12 col-lg-8 animate-on-load fade-in-right" style="animation-delay: 0.3s;">
          <AboutMe />
        </div>
        <div class="col-12 col-md-8 col-lg-4 animate-on-load fade-in-left" style="animation-delay: 0.4s;">
          <TimeZoneCard />
        </div>

        <div class="col-12 col-md-4 col-lg-4 animate-on-load fade-in-right" style="animation-delay: 0.5s;">
          <ContactMe />
        </div>
        <div class="col-12 col-md-12 col-lg-8 animate-on-load fade-in-left" style="animation-delay: 0.6s;"> 
          <div class="row g-4">
          
            <div class="col-12 animate-on-load fade-in-right" style="animation-delay: 0.7s;"> 
              <LocationWeatherCard />
            </div>
            <div class="col-12 animate-on-load fade-in-left" style="animation-delay: 0.8s;">
              <Footer />
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import IntroCard from "./components/IntroCard.vue";
import AboutMe from "./components/AboutMe.vue";
import ContactMe from "./components/ContactMe.vue";
import NowStatusCard from "./components/NowStatusCard.vue";
import TimeZoneCard from "./components/TimeZoneCard.vue";
import LocationWeatherCard from "./components/LocationWeatherCard.vue";
import Footer from "./components/Footer.vue";
</script>



<style scoped>
/* Global styles imported or defined here */
/* @import './style.css'; */ /* If you prefer importing from a separate file */

/* Custom dark theme styles - can also be in style.css */

/* Adjust grid spacing - can also be in style.css */
.container-fluid .row.g-4 {
  /* Target row within container-fluid */
  --bs-gutter-x: 1.5rem; /* Adjust horizontal spacing */
  --bs-gutter-y: 1.5rem; /* Adjust vertical spacing */
}

/* Ensure cards fill grid height - can also be in style.css */
.container-fluid .row.g-4 > [class*="col-"] {
  /* Target columns within row within container-fluid */
  display: flex;
  /* padding handled in global style.css */
}

.container-fluid .row.g-4 > [class*="col-"] > .card {
  /* Target cards within columns... */
  width: 100%;
  height: 100%;
}

/* --- Animation Keyframes --- */
@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(20px); /* Start slightly off-right */
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* --- Apply Animation to Columns --- */
.animate-on-load {
  animation-duration: 0.6s; /* Duration of the animation */
  animation-fill-mode: both; /* Element retains the style values from the last keyframe when the animation ends */
  animation-timing-function: ease-out; /* Animation speed curve */
}

/* Apply specific animation based on class */
.fade-in-left {
  animation-name: fadeInLeft;
   /* Ensure starting position */
   transform: translateX(-20px);
}

.fade-in-right {
  animation-name: fadeInRight;
   /* Ensure starting position */
   transform: translateX(20px);
}

</style>
