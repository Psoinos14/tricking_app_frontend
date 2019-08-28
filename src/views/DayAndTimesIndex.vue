<template>
  <div class="container">
    <h1>All Sessions</h1>
    <div v-for="day_and_time in day_and_times">
      <h2> {{ day_and_time.gym_name}} </h2>
      <p> ID: {{day_and_time.ID}} </p>
      <p> {{ day_and_time.day }} </p>
      <p> {{ day_and_time.date_time}} </p>
      <h3> Attendees: </h3>
      <div v-for="attendee in day_and_time.attendees">
        <p> {{ attendee.first_name }} {{ attendee.last_name }}
        </p>
        <p> Age: {{ attendee.age }}
        </p>
        <p> Location: {{attendee.location}}
        </p>
        <p><button v-on:click="createFriendRequest(attendee.id)">Add Friend</button></p>
        <!-- <div v-if="currentUser === user"> -->
          <!-- <p> user_id: -->
        <p> -------------------------------------------------------  </p>

      </div>
      <!-- <p>
      {{day_and_time.ID}}</p> -->
      <button v-on:click="createAttendee(day_and_time.ID)">Attend This Session</button>
          </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      day_and_times: [],
      attendees: [],
    };
  },
  created: function() {
    axios.get("/api/day_and_times").then(response => {
      this.day_and_times = response.data;
      console.log(response.data)
    });
  },
  methods: {
    createAttendee: function(day_and_timeID) {
      console.log(day_and_timeID);
      var params = {
        day_and_time_id: day_and_timeID
      };
      axios.post("/api/attendees", params).then(response => {
        this.$router.go();
      });
    },
    createFriendRequest: function(friendid) {
      console.log(friendid);
      var params = {
        friend_id: friendid
      };
      axios.post("/friend_requests", params).then(response => {
        this.$router.go();
      });
    }
  }
};
</script>
