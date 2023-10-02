<template>
  <div>
  </div>
  <div>
    <h3>Photos</h3>
    <div v-if="photoUrl">
      <img :src="photoUrl" alt="Sportscar Photo" class="animate__animated animate__fadeIn" style="width: 450px; height: 500px;">
    </div>
    <div v-else>
      <p>No photos found.</p>
    </div>
    <button @click="getNextImage">Next Image</button>
  </div>
</template>

<script>
import axios from "axios";
import 'animate.css';


axios.defaults.headers.common["Authorization"] = "Client-ID awf_ru1bCFchlR67UlHwU1wWtdvCCoswUNC5Mq4cT5o";

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
        .get('https://api.unsplash.com/search/photos', {
          params: {
            query: 'focus st',
          },
        })
        .then(res => {
          const photos = res.data.results;
          const randomIndex = Math.floor(Math.random() * photos.length);
          this.photoUrl = photos[randomIndex].urls.regular;
        })
        .catch(error => {
          console.error("API Error:", error);
        });
    },

  },
  created() {
    this.getNextImage(); 
  },
};


</script>

<style>
button {
  width: 165px;
  height: 62px;
  cursor: pointer;
  color: #fff;
  font-size: 17px;
  border-radius: 1rem;
  border: none;
  position: relative;
  background: #48474b;
  transition: 0.1s;
}

button:after {
  content: '';
  width: 100%;
  height: 100%;
  background-image: radial-gradient(circle farthest-corner at 10% 20%, rgba(255,94,247,1) 17.8%, rgba(2,245,255,1) 100.2%);
  filter: blur(15px);
  z-index: -1;
  position: absolute;
  left: 0;
  right: 0;
}

button:active {
  transform: scale(0.9) rotate(25deg);
  background: radial-gradient(circle farthest-corner at 10% 20%, rgba(255,94,247,1) 17.8%, rgba(2,245,255,1) 100.2%);
  transition: 0.5s;
}


@keyframes jelly {
  0%, 100% {
    transform: scale(1);
  }
  25% {
    transform: scale(1.2);
  }
  75% {
    transform: scale(0.8);
  }
}
</style>
