<template>
  <div class="card text-center ">
    <div class="card-body">
      <p class="card-text">Made with ☕ by <span class="text-green">Karl Chan</span> &copy; {{ currentYear }} </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const currentYear = ref(new Date().getFullYear());
</script>

<style scoped>
.custom-footer {
    background-color: #3a3a3a; /* Match button background or slightly different */
    border-top: 1px solid #4a4a4a; /* Add a subtle border top */
    padding:  1.25rem; /* Adjust padding to match Bootstrap card-footer default */
}
</style>