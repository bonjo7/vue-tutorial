<template>
    <form @submit.prevent="onSubmit">
    <label for="new-todo-input">
      What needs to be done?
    </label>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.lazy.trim="userInput"
    />
    <button type="submit">
      Add
    </button>
  </form>
</template>

<script>

export default {
    methods: {
       onSubmit() {
        // console.log(`user input: ${this.userInput}`)
        if(this.userInput !== ""){
          this.$emit("todo-added", this.userInput);
          this.userInput = "";
        }
       }
   },
  data() {
    return {
      userInput: ""
    };
  }
}
</script>
