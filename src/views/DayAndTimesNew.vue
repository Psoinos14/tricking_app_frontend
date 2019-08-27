<template>
  <div class="container">
    <h1>New Session</h1>
    <form v-on:submit.prevent="createDayAndTime()">
      <ul>
        <li v-for="error in errors"> {{ error}} </li>
      </ul>
      Date and Time:
      <input type="datetime-local" v-model="newDayAndTimeDay" />
      <!-- Time:
      <input type="text" v-model="newDayAndTimeTime" placeholder="blanktime"/> -->
      Gym:
      <input type="text" v-model="newDayAndTimeGymID" />
      <input type="submit" value="Create" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      newDayAndTimeDay: "",
      newDayAndTimeTime: "",
      newDayAndTimeGymID: "",
      errors: []
    };
  },
  // created: function () {
  //   // axios
  //   // .get("/api/day_and_time/" + this.$route.params.id).then(response => {
  //   //   this.day_and_time.user_id = response.data;
  //   });
  // },
  methods: {
    createDayAndTime: function() {
      var params = {
        datetime: this.newDayAndTimeDay,
        
        gym_id: this.newDayAndTimeGymID,
      };
      axios
        .post("/api/day_and_times", params)
        .then(response => {
          this.$router.push("/day_and_times");
        })
        .catch(error => {
          console.log(error.response);
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>
