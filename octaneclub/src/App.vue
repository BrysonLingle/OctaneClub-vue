<template>
<div id="app">
  <h1> Cars </h1>
  <ul>
    <li v-for="item in CarsItems" :key="item.id">
      <cars-item 
      :label="item.label" 
      :done="item.done"
      :id="item.id"></cars-item>
    </li>
  </ul>
</div>

</template>

<script>
import uniqueId from "lodash.uniqueid";
import CarsItem from "./components/CarsItem.vue";
export default {
  name: "app",
  components: {
    CarsItem,
  },
    data() {
    return {
      CarsItems: [
   { id: uniqueId("cars-"), label: "Learn Vue", done: false },
        {
          id: uniqueId("cars-"),
          label: "Create a Vue project with the CLI",
          done: false,
        },
        { id: uniqueId("cars-"), label: "Have fun", done: false },
        { id: uniqueId("cars-"), label: "Create a to-do list", done: false}
      ],
    };
    },
};


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
