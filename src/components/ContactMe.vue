<template>
  <div class="card h-100"> 
    <div class="card-body">
      <h2 class="card-title mb-2">Contact Me</h2>
      <p class="card-text">Feel free to reach out!</p>

      <h4 class="card-subtitle text-muted">Contact Info</h4> 
      <p>📧 {{ email }}</p>
      <p>📲 {{ phone }}</p>
      <p>📍 {{ location }}</p>
      

    </div>

    <div class="card-footer">
        <p>Social Media</p>
      <div class="contact-buttons d-flex gap-2">
        <a
          :href="`mailto:${email}`"
          target="_blank"
          class="btn btn-secondary d-flex align-items-center justify-content-center"
          aria-label="Send Email" 
        >
          <i class="fas fa-envelope"></i>
        </a>

        
        <a
          :href="linkedInUrl"
          target="_blank"
          class="btn btn-secondary d-flex align-items-center justify-content-center"
          aria-label="Visit LinkedIn Profile" 
        >
          <i class="fab fa-linkedin"></i>
        </a>

        
        <a
          :href="githubUrl"
          target="_blank"
          class="btn btn-secondary d-flex align-items-center justify-content-center"
          aria-label="Visit GitHub Profile" 
        >
          <i class="fab fa-github"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const email = ref("ryzen.script@gmail.com");
const phone = ref("+1 604 908 2360");
const location = ref("Vancouver, Canada");
const linkedInUrl = ref("https://www.linkedin.com/in/karl-chan-5785a62a8/");
const githubUrl = ref("https://github.com/ryzen852");
</script>

<style scoped>
/* Add component specific styles here */

/* Style for the card footer */
.card-footer {
    background-color: #3a3a3a; /* Match button background or slightly different */
    border-top: 1px solid #4a4a4a; /* Add a subtle border top */
    padding: 0.75rem 1.25rem; /* Adjust padding to match Bootstrap card-footer default */
}

.contact-buttons {
  /* d-flex and gap-2 are handled by Bootstrap classes in the template */
  flex-wrap: wrap; /* Allow buttons to wrap */
}

.contact-buttons .btn {
  /* Make buttons square */
  width: 40px; /* Adjusted size slightly */
  height: 40px; /* Adjusted size slightly */
  padding: 0;
  background-color: #2a2a2a; /* Match card body background */
  border-color: #3a3a3a; /* Match card footer background */
  color: #f0f0f0;
  border-radius: 8px;
  transition: background-color 0.3s ease, border-color 0.3s ease;
}

.contact-buttons .btn:hover {
  background-color: #4a4a4a;
  border-color: #5a5a5a;
  color: #ffffff;
}

.contact-buttons .btn i {
  font-size: 1.3rem; /* Adjusted icon size */
}

/* Adjust spacing between contact info and buttons */
.card-body p:last-of-type {
    margin-bottom: 1rem; /* Add some space below the last paragraph before the footer */
}

</style>
