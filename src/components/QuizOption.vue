<template>
  <label :class="{ 'disabled': disabled }">
    <input
      type="radio"
      :value="option"
      :name="'q' + questionId"
      :checked="selected"
      :disabled="disabled"
      @change="$emit('change', option)" />

      {{ option.name }}
  </label>
</template>

<script>
export default {
  name: 'quiz-option',

  props: {
    option: Object,
    disabled: Boolean,
    selected: Boolean,
    questionId: Number
  }
}
</script>

<style lang="scss" scoped>
.disabled {
  opacity: 0.5;
}
</style>
