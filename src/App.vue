<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="setAge">Set Age</button>

    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">Set Name</button>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, computed, watch } from 'vue';

let firstName = ref('');
let lastName = ref('');
let lastNameInput = ref(null);

const user = reactive({
  userName: 'Brad',
  age: 33,
});

const userName = computed(() => `${firstName.value} ${lastName.value}`);

watch([user, userName], (newValues, oldValues) => {
  console.log(newValues[0].age, oldValues[0].age);
  console.log(newValues[1], oldValues[1]);
});

setTimeout(() => {
  user.userName = 'Bradley';
  user.age = 50;
}, 2000);

function setAge() {
  user.age = 34;
}

function setLastName() {
  lastName.value = lastNameInput.value.value;
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
