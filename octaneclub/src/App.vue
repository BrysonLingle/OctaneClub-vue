<template>
<div id="app">
  <h1> Cars </h1>
  <post-form @newpost-added="addNewPost"></post-form>
    <li v-for="item in CarsItems" :key="item.id">
      <cars-item 
      :label="item.label" 
      :done="item.done"
      :id="item.id"></cars-item>
    </li>
</div>
<p>Dark theme: {{isDark}}</p>

<button @click="toggleDark()">
  Toggle Color Mode
</button>

</template>

<script>
import uniqueId from "lodash.uniqueid";
import PostForm from "./components/NewPost.vue";
import CarsItem from "./components/CarsItem.vue";


export default {
  name: "app",
  components: {
    CarsItem,
    PostForm,
  },
  data() {
    return {
      CarsItems: [],
    };
  },
  methods: {
    addNewPost(newPostLabel) {
      this.CarsItems.push({ id: uniqueId("newpost-"), label: newPostLabel, done: false, comment: "" });
    },
    saveComment() {
      // You can add logic related to saving comments here if needed.
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}

  /* Global styles */
  .dark {
  background: #16171d; 
  color: #fff;
}

  

  .label-wrapper {
    margin: 0;
    flex: 0 0 100%;
    text-align: center;
  }
  [class*="__lg"] {
    display: inline-block;
    width: 100%;
    font-size: 1.9rem;
  }
  [class*="__lg"]:not(:last-child) {
    margin-bottom: 1rem;
  }
  @media screen and (min-width: 620px) {
    [class*="__lg"] {
      font-size: 2.4rem;
    }
  }
  .visually-hidden {
    position: absolute;
    height: 1px;
    width: 1px;
    overflow: hidden;
    clip: rect(1px 1px 1px 1px);
    clip: rect(1px, 1px, 1px, 1px);
    clip-path: rect(1px, 1px, 1px, 1px);
    white-space: nowrap;
  }
  [class*="stack"] > * {
    margin-top: 0;
    margin-bottom: 0;
  }
  .stack-small > * + * {
    margin-top: 1.25rem;
  }
  .stack-large > * + * {
    margin-top: 2.5rem;
  }
  @media screen and (min-width: 550px) {
    .stack-small > * + * {
      margin-top: 1.4rem;
    }
    .stack-large > * + * {
      margin-top: 2.8rem;
    }
  }
  /* End global styles */
  #app {
    background: #404040;
    margin: 2rem 0 4rem 0;
    padding: 1rem;
    padding-top: 0;
    position: relative;
    box-shadow:
      0 2px 4px 0 rgba(0, 0, 0, 0.2),
      0 2.5rem 5rem 0 rgba(0, 0, 0, 0.1);
  }
  @media screen and (min-width: 550px) {
    #app {
      padding: 4rem;
    }
  }
  #app > * {
    max-width: 50rem;
    margin-left: auto;
    margin-right: auto;
  }
  #app > form {
    max-width: 100%;
  }
  #app h1 {
    display: block;
    min-width: 100%;
    width: 100%;
    text-align: center;
    margin: 0;
    margin-bottom: 1rem;
  }
</style>


