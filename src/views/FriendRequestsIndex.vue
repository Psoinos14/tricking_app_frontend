<template>
  <div class="container">
    <h1> All Incoming Friend Requests </h1>
    <div v-for="friend_request in friend_requests">
      <p> {{friend_request.incoming}} </p>
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
    submit: function() {

      var params = {
        user_id: this.user_id
      };
      axios.post("/friendships", params).then(response => {
        this.friend_requests = response.data;
        console.log(this.friend_requests);
      });
    }
  }
};
</script>