<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <input type="text" v-model="newStatusText" placeholder="Land a new trick?"/> 
    <button v-on:click="createStatus()">Post Status</button>
    <h2>{{message3}}</h2>
    <div v-for="status in myStatuses">
        <p> {{status.text}}</p>
    </div>
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
      message3: "Your recent posts and accomplishments",
      friends: [],
      newStatusText: "",
      myStatuses: [],
      errors: [],
    };
  },
  created: function() {
    axios.get("/api/statuses").then(response => {
      // const new_friends = response.data[1];
      // const myStatuses = response.data[0];
      // myStatuses.forEach(status => {
      //   this.statuses.push(status);
      // });
      // new_friends.forEach(friend => {
      //   this.friends.push(friend);
      // });

      
      
      this.friends = (response.data[1]);
      this.myStatuses = response.data[0]['statuses'];
      // this.friends = response.data;
      console.log(this.allStatuses);
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
          this.myStatuses.push(response.data);
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