<template>
  <div v-if="!loading">
    <button @click="addit">sdasdsad</button>
    <survey :survey="survey" />
  </div>
</template>

<script>
import * as Survey from "survey-vue";
import "survey-vue/modern.css";
import "./index.css";
Survey.settings.lazyRowsRendering = true;
Survey.StylesManager.applyTheme("modern");
const json = require("../components/survey.json");
const answers_test = require("../components/answers_test.json");

export default {
  name: "surveyjs-component",
  data(cmp) {
    let loading = true;
    let survey = {};
    let doStuff = async () => {};
    survey = new Survey.Model(json);
    survey.data = answers_test;
    doStuff().then((r) => {
      cmp.loading = false;
    });
    doStuff().then((el) => {
      //cmp.survey.data = answers_test;
    });
    return {
      loading,
      survey,
    };
  },
  mounted() {
    //this.survey.data = answers_test;
  },
  methods: {
    callme() {
      console.log("created");
    },
    addit(sur) {
      this.survey.data = answers_test;
    },
    watch: {
      loading() {
        this.survey.data = answers_test;
      },
    },
  },
};
</script>

<style scoped>
</style>
