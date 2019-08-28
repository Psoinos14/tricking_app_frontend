<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <input type="text" v-model="newStatusText" placeholder="Land a new trick?"/> 
    <button v-on:click="createStatus()">Post Status</button>
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
      const new_friends = response.data;
      new_friends.forEach(friend => {
        this.friends.push(friend)
      })
      console.log(response.data);
      // this.friends = response.data;
    });
  },
  methods: {
    createStatus: function() {
      var params = {
        text: this.newStatusText
      };
      axios
        .post("/api/statuses", params)
        .then(response => { 
          const newStatus = response.data
          console.log(newStatus)
          // add this to the current user's statuses array using push
        })
        .catch(error => {
          console.log(error.response);
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>