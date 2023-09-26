<template>
  <form @submit.prevent="onSubmit">
    <label for="new-post-input">Add A New Post!</label>
    <input
      type="text"
      id="new-post-input"
      name="new-post"
      autocomplete="off"
      v-model.lazy.trim="label"
    />
    <button type="submit">Add</button>
  
  </form>
</template>




<script>
export default {
  methods: {
    onSubmit() {
  if (this.label === "") {
    return;
  }
  this.$emit('newpost-added', this.label);
  this.label = "";
},
  },
};



</script>
