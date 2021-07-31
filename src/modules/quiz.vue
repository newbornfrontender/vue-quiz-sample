<template>
  <div v-if="!isResult">
    <Question
      v-for="(question, index) in questions"
      v-show="count === index"
      :key="question.id"
      :question="question"
      :select-item="selectItem"
    />

    <div>
      <button v-if="count > 0" @click="prev">Назад</button>
      <button v-if="count !== questions.length - 1" @click="next">Вперед</button>
      <button v-else @click="showResult">Показать результат</button>
    </div>
  </div>
  <div v-else>
    <Report :questions="questions" :answers="answers" />

    <button @click="reset">Заново</button>
  </div>
</template>

<script>
import Question from '../components/question.vue';
import Report from '../components/report.vue';

export default {
  components: {
    Question,
    Report,
  },

  data() {
    return {
      count: 0,

      isResult: false,

      answers: {},

      questions: [
        {
          id: 0,
          title: 'Столица Австралии?',
          answers: [
            {
              id: 0,
              title: 'Канберра',
              isCorrect: true,
            },
            {
              id: 1,
              title: 'Сидней',
              isCorrect: false,
            },
            {
              id: 2,
              title: 'Мельбурн',
              isCorrect: false,
            },
          ],
        },
        {
          id: 1,
          title: 'Столица Японии?',
          answers: [
            {
              id: 3,
              title: 'Саппоро',
              isCorrect: false,
            },
            {
              id: 4,
              title: 'Киото',
              isCorrect: false,
            },
            {
              id: 5,
              title: 'Токио',
              isCorrect: true,
            },
          ],
        },
      ],
    };
  },

  methods: {
    next() {
      if (this.count < this.questions.length - 1) this.count++;
    },

    prev() {
      if (this.count > 0) this.count--;
    },

    reset() {
      this.count = 0;
      this.isResult = false;
    },

    selectItem(question, answer) {
      this.answers[question] = answer;
    },

    showResult() {
      this.isResult = true;
    },
  },
};
</script>
