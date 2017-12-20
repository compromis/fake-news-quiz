<template>
  <div class="question-wrapper">
    <h3>{{ question.name }}</h3> {{ selectedOption }}
    <div v-for="option in question.options">
      <li>
        <label>
          <input type="radio" :value="option" v-model="selectedOption" /> {{ option.name }}
        </label>
      </li>
    </div>
  </div>
</template>

<script>
export default {
  name: 'question',

  props: {
    question: Object
  },

  data () {
    return {
      selectedOption: null
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
