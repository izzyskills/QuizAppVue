<script setup>
import Result from "../components/Result.vue";
import Question from "../components/Question.vue";
import QuestionHeader from "../components/QuestionHeader.vue";
import { useRoute } from "vue-router";
import { ref, computed } from "vue";
import quizzes from "../data/quizzes.json";
const route = useRoute();
const quizID = parseInt(route.params.id);
const quiz = quizzes.find((q) => q.id === quizID);
const currentQuestionIndex = ref(0);
const numberOfCorrectAnswers = ref(0);
const showResult = ref(false);
const questionStatus = computed(
  () => `${currentQuestionIndex.value}/${quiz.questions.length}`
);
const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);
const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++;
  }
  if (currentQuestionIndex.value < quiz.questions.length - 1) {
    currentQuestionIndex.value++;
  } else {
    showResult.value = true;
    currentQuestionIndex.value++;
  }
};
</script>
<template>
  <div>
    <QuestionHeader
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"
    />
    <div>
      <Result
        v-if="showResult"
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
        :questionLength="quiz.questions.length"
      />
      <Question
        v-else
        :question="quiz.questions[currentQuestionIndex]"
        @SelectOption="onOptionSelected"
      />
    </div>
  </div>
</template>
