<template>
  <div v-if="!loading">
    <h1>we are loaded</h1>
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
    doStuff().then((r) => {
      cmp.survey = new Survey.Model(json);
      cmp.loading = false;
      cmp.survey.data = answers_test;
    });
    return {
      loading,
      survey,
    };
  },
  mounted() {},
};
</script>

<style scoped>
</style>
