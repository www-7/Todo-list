<template>
  <div class="fields">
    <input
      type="text"
      v-model.trim="text"
      v-focus />
    <button @click="addTodo">
      <img
        src="../assets/Vector.png"
        alt="add" />
    </button>
  </div>
</template>

<script>
import focusDirective from './focusDirective';
  export default {
    directives: {
      focus: focusDirective
    },
    data() {
      return {
        text: null,
      };
    },
    methods: {
      addTodo() {
        if (this.text !== null) {
          this.$emit('add-todo', this.text);
          this.text = null;
        }
      },
    },
  };
</script>

<style scoped>
  .fields {
    display: flex;
    margin-bottom: 15px;
    width: 100%;
  }
  button {
    background: #13e328;
    border: none;
    width: 44px;
    height: 44px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  input {
    border: 1px solid #e1e1e1;
    background: #ffffff;
    width: 100%;
    height: 40px;
  }
</style>
