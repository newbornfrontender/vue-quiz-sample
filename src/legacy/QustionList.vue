<template>
  <div>
    <label>
      <input type="radio" value="correct" name="inputName" @click="selectItem(questText, correct)" />

      {{ questText }}
    </label>
  </div>
</template>

<script>
export default {
  props: ['quest-text', 'correct', 'input-name', 'check-field', 'select-item'],
};
</script>
