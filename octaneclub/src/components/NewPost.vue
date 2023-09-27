<template>
  <form @submit.prevent="onSubmit">
    <h2 class="label-wrapper">
    <label for="new-post-input">Add A New Post!</label>
    </h2>
    <input
      type="text"
      id="new-post-input"
      name="new-post"
      autocomplete="off"
      v-model.lazy.trim="label"
    class="input_lg"/>
    <button type="submit" class="btn btn__primary btn__lg">Add</button>

  
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
