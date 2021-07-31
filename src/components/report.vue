<template>
  <div>
    <h1>Результаты</h1>

    <ul v-for="(question, index) in questions" :key="question.id">
      <li>{{ question.title }}</li>

      <ul>
        <li
          v-for="answer in question.answers"
          :key="answer.id"
          :class="{
            correct: answer.id === answers[index] && answer.isCorrect,
            incorrect: answer.id === answers[index] && !answer.isCorrect,
          }"
        >
          {{ answer.title }}
        </li>
      </ul>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['questions', 'answers'],
};
</script>

<style scoped>
ul ul li {
  color: #757575;
}

.correct {
  color: green;
}

.incorrect {
  color: red;
}
</style>
