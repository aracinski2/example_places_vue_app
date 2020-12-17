<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="place in places">
      <h4>{{ place.name }}</h4>
      <h5>{{ place.address }}</h5>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!!!!!!!!!!",
      places: [],
      name: "",
      address: "",
    };
  },
  created: function () {
    console.log("in created");
    this.indexPlaces();
  },
  methods: {
    indexPlaces: function () {
      console.log("places index");
      axios.get("/api/places").then((response) => {
        console.log(response.data);
        this.places = response.data;
      });
    },
    // createPlaces: function () {
    //   console.log("create place");
    //   axios.post("/api/places").then((response) => {
    //     console.log();
    //   });
    // },
  },
};
</script>