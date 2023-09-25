<script setup>
import { ref, watch } from "vue";
import q from "../data/quizzes.json";
import Card from "../components/Card.vue";
const quizzes = ref(q);
const search = ref("");
watch(search, () => {
  quizzes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>
<template>
  <header>
    <h1>Quizzes</h1>
    <input v-model.trim="search" type="text" placeholder="Search..." />
  </header>
  <div class="option-container">
    <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
  </div>
</template>
<style scoped>
header {
  margin-top: 30px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}
header h1 {
  font-weight: bold;
  margin-right: 30px;
}
header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}
.option-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
