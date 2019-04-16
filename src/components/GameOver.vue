<template>
  <div>
    <b-jumbotron>
      <h2>Game Over!</h2>
      <p>You got {{ numberOfCorrectAnswers }} answers correct out of {{ numberOfTotalAnswers }} questions!</p>
      <p>Play Again?</p>
      <button @click="newQuestions">Replay Game!</button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    numberOfCorrectAnswers: Object,
    numberOfTotalAnswers: Object,
    newQuestions: Function
  }
};
</script>

<style scoped>
</style>
