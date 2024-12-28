<template>
  <div class="field">
    <input
      type="text"
      v-model.trim="text" />
    <button @click="addTodo">
      <img
        src="../assets/Vector.png"
        alt="add" />
    </button>
  </div>
</template>

<script>
  export default {
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
  button {
    background: #13e328;
    border: none;
    width: 44px;
    height: 44px;
    cursor: pointer;
  }
  input {
    border: 1px solid #e1e1e1;
    background: #ffffff;
    width: 350px;
    height: 40px;
  }
  .field {
    display: flex;
    /* justify-content: center; */
    margin-bottom: 15px;
    width: 390px;
  }
</style>
