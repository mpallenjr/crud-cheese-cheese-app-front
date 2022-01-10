<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="cheese in cheeses">
      <h1>{{cheese.name}}</h1>
      <h3>{{cheese.origin}}</h3>
      <h3>{{cheese.milk}}</h3>
      <h3>{{cheese.firmness}}</h3>
      <img v-bind:src="cheese.image_url">
    </div>
  </div>
</template>

<style></style>

<script>
import axios from 'axios';
  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js!",
        cheeses: []
      };
    },
    created: function () {
      axios.get("http://localhost:3000/cheeses").then(response => {
        console.log(response.data)
        this.cheeses = response.data
      })
    },
    methods: {},
  };
</script>