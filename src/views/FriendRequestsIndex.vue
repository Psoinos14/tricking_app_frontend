<template>
  <div class="container">
    <h1> All Incoming Friend Requests </h1>
    <div v-for="friend_request in friend_requests">
      <p> {{friend_request.incoming_friend_requests}} </p>
      <button v-on:click="createFriendship(friend_request.friend_id)">Accept Friend Request</button>
      <!-- <button v-on:click="destroyFriendRequest()">Deny Friend Request</button> -->
    </div>
  </div>


</template>
<script>
import axios from "axios";

export default {
  data: function() {
    return {
      friend_requests: []
    };
  },
  created: 


  function() {
    axios.get("/friend_requests").then(response => {
      this.friend_requests = response.data;
      console.log(this.friend_requests);
    });
  },

  methods: {
    createFriendship: function(id) {
      console.log(id)

      var params = {
        user_id: id
      };
      axios.post("/friendships", params).then(response => {
        this.friend_requests = response.data;
        console.log(this.friend_requests);
      });
    }
  }
};
</script>