<template>
  <h2>{{ name }}</h2>
  <h3>{{ age }}</h3>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const props = defineProps(['firstName', 'lastName', 'age']);

const name = computed(() => `${props.firstName} ${props.lastName}`);

// export default {
//   props: ['firstName', 'lastName', 'age'],
//   computed: {
//     name() {
//       return `${this.firstName} ${this.lastName}`;
//     }
//   }
// };
</script>
