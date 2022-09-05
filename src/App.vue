<template>
  <section class="container">
    <h2>{{ user.userName }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="setAge">Set Age</button>
  </section>
</template>

<script setup>
import { reactive } from 'vue';

const user = reactive({
  userName: 'Brad',
  age: 33,
});

setTimeout(() => {
  user.userName = 'Bradley';
  user.age = 50;
}, 2000);

function setAge() {
  user.age = 34;
}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
