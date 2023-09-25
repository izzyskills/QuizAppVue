<script setup>
import { useRouter } from "vue-router";
const router = useRouter();
const { numberOfCorrectAnswers, questionLength } = defineProps([
  "numberOfCorrectAnswers",
  "questionLength",
]);
</script>
<template>
  <div class="results">
    <p>Your Results...</p>
    <h1>{{ numberOfCorrectAnswers }}/{{ questionLength }}</h1>
    <button @click="router.push('/')">Go Back</button>
  </div>
</template>
<style scoped>
.results {
  text-align: center;
  padding: 100px;
}
p {
  font-size: 2.4em;
}
h1 {
  font-size: 5em;
}

button {
  all: unset;
  margin: 40px;
  padding: 100px auto;
  border-radius: 4px;
  border-color: none;
  background-color: rgba(217, 40, 40, 0.757);
  text-align: center;
  font-size: 2em;
  padding: 0.3em;
}
</style>
