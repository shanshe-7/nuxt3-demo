<script setup>
import { ref, computed, watchEffect } from "vue";

import { useRoute } from "vue-router";

const route = useRoute();

let photos = ref([]);

let numberOfPhotos = computed(function () {
  return displayPhotos.value.length;
});

let displayPhotos = computed(function () {
  if (route.query.even) {
    return photos.value.filter((_, i) => i % 3 === 0);
  } else {
    return photos.value;
  }
});

onMounted(() => {
  fetch("https://jsonplaceholder.typicode.com/photos")
    .then((res) => res.json())
    .then((jsonRes) => {
      photos.value = jsonRes;
    })
    .catch((err) => {
      console.log(err);
    });
});
</script>

<template>
  <div>
    <br />
    <p>{{ numberOfPhotos }} photos</p>
    <!-- <pre>{{ displayPhotos }}</pre> -->

    <div>
      <span v-for="photo in displayPhotos" :key="photo.id">
        <img :src="photo.thumbnailUrl" />
      </span>
    </div>
  </div>
</template>
