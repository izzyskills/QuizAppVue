<script setup>
const { question } = defineProps(["question"]);
const emit = defineEmits(["SelectOption"]);

const emitSelectedOption = (isCorrect) => {
  emit("SelectOption", isCorrect);
};
</script>
<template>
  <div class="question-container">
    <h1 class="question">{{ question.text }}</h1>
  </div>
  <div class="option-container">
    <div
      v-for="option in question.options"
      :key="option.id"
      class="option"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">
        <p>{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.question-container {
  margin-top: 20px;
}
.question {
  font-size: 3em;
  margin-bottom: 20px;
}
.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}
.option-label {
  background-color: rgba(0, 144, 98, 0.878);
  width: 40px;
  height: 40px;
  font-size: 2.5em;
  display: flex;
  align-items: center;
  justify-content: center;
}
.option-value {
  background-color: rgba(70, 70, 70, 0.878);
  width: 100%;
  font-size: 1.7em;
  padding: 0 20px;
}
</style>
