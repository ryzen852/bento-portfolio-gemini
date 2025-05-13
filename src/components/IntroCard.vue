<template>
  <div class="card text-center">
    <div class="card-body">
      <img
        :src="imgUrl"
        class="rounded-circle mb-3"
        style="width: 200px; height: 200px; object-fit: cover"
      />
      <h1 class="card-title">Karl Chan</h1>
      <p class="card-text text-green">Full Stack Developer</p>
      <p class="card-text text-muted">
        Hi <span id="wave">👋</span> I’m Karl Chan — a full stack developer with
        expertise in both frontend and backend technologies. I’m passionate
        about building scalable applications with clean, reusable code, and I
        stay up to date with modern development practices and tools.
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const imgUrl = new URL('../assets/intro.jpeg', import.meta.url).href
</script>
