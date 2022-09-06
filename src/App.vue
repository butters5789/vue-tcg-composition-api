<template>
  <section class="container">
    <user-data :first-name="firstName" :last-name="lastName"></user-data>
    <button @click="setAge">Set Age</button>

    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">Set Name</button>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, watch, provide } from 'vue';
import UserData from './components/UserData.vue';

let age = ref(33);
let firstName = ref('');
let lastName = ref('');
let lastNameInput = ref(null);

let userName = computed(() => `${firstName.value} ${lastName.value}`);

setTimeout(() => {
  age.value = 50;
}, 2000);

function setAge() {
  age.value = 34;
}

function setLastName() {
  lastName.value = lastNameInput.value.value;
}

provide('age', age);

watch([age, userName], (newValues, oldValues) => {
  console.log(newValues[0], oldValues[0]);
  console.log(newValues[1], oldValues[1]);
});
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
