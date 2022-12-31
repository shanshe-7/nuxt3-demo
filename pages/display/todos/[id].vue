<script setup>
import { useRoute } from "vue-router";
const route = useRoute();
</script>

<template lang="">
  <div>{{ route.params.id }}</div>
</template>

<style lang=""></style>
