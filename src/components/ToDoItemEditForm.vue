<template>
  <form class="stack-small" @submit.prevent="onSubmit">
    <div>
      <label class="edit-label">Edit Name for &quot;{{userInput}}&quot;</label>
      <input :id="id" type="text" autocomplete="off" v-model.lazy.trim="newUserInput" ref="labelInput" />
    </div>
    <div class="btn-group">
      <button type="button" class="btn" @click="onCancel">
        Cancel
        <span class="visually-hidden">editing {{userInput}}</span>
      </button>
      <button type="submit" class="btn btn__primary">
        Save
        <span class="visually-hidden">edit for {{userInput}}</span>
      </button>
    </div>
  </form>
</template>
<script>
export default {
  props: {
    userInput: {
      type: String,
      required: true
    },
    id: {
      type: String,
      required: true
    }
  },
  mounted() {
    const labelInputRef = this.$refs.labelInput;
    labelInputRef.focus();
    },
  data() {
    return {
      newUserInput: this.userInput
    };
  },
  methods: {
    onSubmit() {
      if (this.newUserInput && this.newUserInput !== this.userInput) {
        this.$emit("item-edited", this.newUserInput);
      }
    },
    onCancel() {
      this.$emit("edit-cancelled");
    }
  }
};
</script>
<style scoped>
.edit-label {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #0b0c0c;
  display: block;
  margin-bottom: 5px;
}
input {
  display: inline-block;
  margin-top: 0.4rem;
  width: 100%;
  min-height: 4.4rem;
  padding: 0.4rem 0.8rem;
  border: 2px solid #565656;
}
form {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
form > * {
  flex: 0 0 100%;
}
</style>