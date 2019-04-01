<template>
  <div>
    <b-jumbotron>
      <template slot="lead">{{ currentQuestion.question }}</template>

      <hr class="my-4">

      <b-list-group>
        <b-list-group-item v-for="answer in answers" :key="answer">{{ answer }}</b-list-group-item>
      </b-list-group>

      <b-button variant="primary">Submit</b-button>
      <b-button @click="next" variant="success">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  computed: {
    answers() {
      let answers = [...this.currentQuestion.incorrect_answers];
      answers.push(this.currentQuestion.correct_answer);
      return answers;
    }
  },
  mounted() {
    console.log(this.currentQuestion);
  }
};
</script>
