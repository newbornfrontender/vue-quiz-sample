<template>
  <div>
    <div v-for="(item, index) in questions" :key="index">
      <div v-show="index === count">
        <h1>
          {{ item.text }}
        </h1>

        <div class="quest-list" v-for="(quest, index) in item.responses" :key="index">
          <question-list
            :quest-text="quest.text"
            :correct="quest.correct"
            :input-name="index"
            :check-field="quest.correct"
            :select-item="selectItem"
          >
          </question-list>
        </div>

        <div>
          <button @click="next">next</button>
        </div>
      </div>
    </div>

    <div v-show="count === questions.length">
      <Result :result="answers" />
    </div>
  </div>
</template>

<script>
import QuestionList from './QustionList.vue';
import Result from './Result.vue';

export default {
  components: {
    QuestionList,
    Result,
  },
  data() {
    return {
      questions: [
        {
          text: 'Первый вопрос',
          responses: [
            {
              text: 'Неправильный ответ1',
              correct: false,
            },
            {
              text: 'Правильный ответ!1',
              correct: true,
            },
          ],
        },
        {
          text: 'Второй вопрос',
          responses: [
            {
              text: 'Правильный ответ2',
              correct: true,
            },
            {
              text: 'Не правильный ответ2',
              correct: false,
            },
          ],
        },
      ],

      results: '',

      count: 0,

      answers: [],
    };
  },

  methods: {
    next() {
      this.count++;
    },

    score: function () {
      return this.userResponses.filter(function (val) {
        return val;
      }).length;
    },

    selectItem(text, correct) {
      this.answers = [...this.answers, { text, correct }];
    },
  },
};
</script>
