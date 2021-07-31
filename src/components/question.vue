<template>
  <section>
    <h2>{{ question.title }}</h2>

    <Answer
      v-for="{ title, id, isCorrect } in question.answers"
      :key="id"
      :answer-id="id"
      :question-id="question.id"
      :title="title"
      :isCorrect="isCorrect"
      :select-item="selectItem"
    />
  </section>
</template>

<script>
import Answer from './answer.vue';

export default {
  components: {
    Answer,
  },

  props: ['question', 'select-item'],
};
</script>
