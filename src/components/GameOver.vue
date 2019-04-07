<template>
  <div>
    <b-jumbotron>
      <h2>Game Over!</h2>
      <p>You got {{ numberOfCorrectAnswers }} answers correct out of {{ numberOfTotalAnswers }} questions!</p>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: ["numberOfCorrectAnswers", "numberOfTotalAnswers"]
};
</script>

<style scoped>
</style>
