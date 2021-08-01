<template>
  <div>
    <h1>Опрос закончен</h1>

    <ul>
      <li v-for="{ text, correct } in result" :key="text" :class="{ correct, incorrect: !correct }">{{ text }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['result'],
};
</script>

<style scoped>
ul {
  display: flex;
  flex-direction: column;
}

.correct {
  color: green;
}

.incorrect {
  color: red;
}
</style>
