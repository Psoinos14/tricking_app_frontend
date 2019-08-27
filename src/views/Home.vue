<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <button v-on:click="createStatus()">What have you been up to?</button>
    <h2>{{message2}}</h2>
    <div v-for="status in statuses">
      <h5>Tricker: {{status.user}} </h5>
      <p> {{status.text}} </p>
      <p> ------------------------------------------------------- </p>
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
  methods: {
    createStatus: function() {
      var newStatus = {
        Text: this.newText,
        User: this.currentuser
        // Day: this.newDayAndTimeDay,
        // Time: this.newDayAndTimeTime,
        // Gym: this.newDayAndTimeGymID,
      };
    }
  }
};
</script>