<template>
  <label>
    <input type="radio" name="answers" :value="answerId" @click="selectItem(questionId, answerId)" />

    <p>{{ title }}</p>
  </label>
</template>

<script>
export default {
  props: ['title', 'answerId', 'questionId', 'isCorrect', 'index', 'select-item'],
};
</script>

<style scoped>
input,
p {
  margin: 0;
}

p {
  margin-inline-start: 10px;
}

label {
  display: flex;
  align-items: center;
  margin: 10px 0;
}
</style>
