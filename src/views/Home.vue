<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <input type="text" v-model="newStatusText" placeholder="Land a new trick?"/> 
    <button v-on:click="createFriends()">Post Status</button>
    <h2>{{message2}}</h2>
    <div v-for="friend in friends">
      <h5>Tricker: {{friend.user}} </h5>
      <div v-for="status in friend.statuses">
      <p> {{status.text}} </p>
      <p> ------------------------------------------------------- </p>
    </div>
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
      friends: [],
      newStatusText: "",

      errors: [],
    };
  },
  created: function() {
    axios.get("/api/statuses").then(response => {
      console.log(response.data);
      this.friends = response.data;
    });
  },
  methods: {
    createFriends: function() {
      var params = {
        text: this.newStatusText
      };
      axios
        .post("/api/statuses", params)
        .then(response => {
          
        })
        .catch(error => {
          console.log(error.response);
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>