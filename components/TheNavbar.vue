<script setup>
import { ref } from "vue";
const evenCheck = ref(false);
</script>

<template lang="">
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-start">
      <NuxtLink to="/" class="navbar-item"> Home </NuxtLink>

      <NuxtLink to="/display" class="navbar-item"> Display </NuxtLink>
      <NuxtLink to="/display/todos" class="navbar-item"> Todo </NuxtLink>

      <NuxtLink to="/display/photos" class="navbar-item"> Photo </NuxtLink>

      <NuxtLink to="/display/photos?even=true" class="navbar-item">
        even photos
      </NuxtLink>
    </div>
  </nav>
</template>

<style lang=""></style>
