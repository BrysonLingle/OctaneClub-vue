<template>
  <div>
    <h3>Photos</h3>
    <div v-if="photoUrl">
      <img :src="photoUrl" alt="Dog Photo">
    </div>
    <div v-else>
      <p>No photos found.</p>
    </div>
    <button @click="getNextImage">Next Image</button>
  </div>
</template>

<script>
import axios from "axios";


export default {
  name: "PhotosRandom",
  data() {
    return {
      photoUrl: null,
    };
  },
  methods: {
    getNextImage() {
      axios
        .get('https://dog.ceo/api/breeds/image/random')
        .then(res => {
          this.photoUrl = res.data.message; 
        })
        .catch(error => {
          console.error("API Error:", error);
        });
    },
  },
  created() {
    this.getNextImage(); // Load the first image when the component is created
  },
};
</script>
<style>
button {
  background-color: #000000; /* Blue background color */
  color: #fff; /* White text color */
  padding: 10px 20px; /* Padding around the text */
  border: none; /* No border */
  cursor: pointer; /* Cursor style on hover */
}

button:hover {
  background-color: #000000; 
  color: white;
  box-shadow: 0 0 0 18px transparent;
      animation: jelly 1s;
}
</style>
