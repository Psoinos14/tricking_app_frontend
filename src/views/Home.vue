<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>{{message2}}</h2>
    <div v-for="status in statuses">
      <h5>Tricker: {{status.user}} </h5>
      <p> {{status.text}} </p>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to TrickTogether!",
      message2: "See what other trickers have been up to:",
      statuses: [],
    };
  },
  created: function() {
    axios.get("/api/statuses").then(response => {
      this.statuses = response.data;
    });
  },
  methods: {}
};
</script>