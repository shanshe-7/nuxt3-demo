<script setup>
import { ref } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();

defineProps({
  title: {
    type: String,
    default: "Hello World",
  },
});

let todoList = ref([]);

fetch("https://jsonplaceholder.typicode.com/todos")
  .then((res) => res.json())
  .then((jsonRes) => {
    todoList.value = jsonRes;
  })
  .catch((err) => {
    console.log(err);
  });
</script>

<template>
  <div>
    <br />

    <h1 class="title">{{ title }}</h1>
    <slot name="hero" />

    <slot name="separator" />

    <ul class="list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /><NuxtLink
          :to="`/display/todos/${todo.id}`"
          >{{ todo.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
@import "./assets/styles/main.scss";

:root {
  --text-color: #{$textColor};
}
.heading {
  color: var(--text-color);
}
.list {
  color: var(--text-color);
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
