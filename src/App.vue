<template>
  <div id="app">
    <Header
      :numberOfCorrectAnswers="numberOfCorrectAnswers"
      :numberOfTotalAnswers="numberOfTotalAnswers"
    />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
            v-if="numberOfTotalAnswers < 10"
            :currentQuestion="questions[index]"
            :next="next"
            :increment="increment"
          />
          <GameOver
            v-if="numberOfTotalAnswers === 10"
            :numberOfCorrectAnswers="numberOfCorrectAnswers"
            :numberOfTotalAnswers="numberOfTotalAnswers"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import QuestionBox from "./components/QuestionBox.vue";
import GameOver from "./components/GameOver.vue";

export default {
  name: "app",
  components: {
    Header,
    QuestionBox,
    GameOver
  },
  data() {
    return {
      questions: [],
      index: 0,
      numberOfCorrectAnswers: 0,
      numberOfTotalAnswers: 0
    };
  },
  methods: {
    next() {
      this.index++;
    },
    increment(isCorrect) {
      if (isCorrect) {
        this.numberOfCorrectAnswers++;
      }
      this.numberOfTotalAnswers++;
    }
  },
  mounted: function() {
    fetch("https://opentdb.com/api.php?amount=10&category=27&type=multiple", {
      method: "get"
    }).then(response => {
      return response.json().then(jsonData => {
        this.questions = jsonData.results;
      });
    });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
