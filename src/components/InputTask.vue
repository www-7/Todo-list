<template>
  <div class="field">
    <input
      type="text"
      v-model.trim="task"
      v-focus
      @keyup.enter="task"
    />
    <button @click="addTask">
      <img
        src="../assets/Vector.png"
        alt="add"
      />
    </button>
  </div>
</template>

<script>
import focusDirective from './focusDirective';
export default {
  directives: focusDirective,
  data() {
    return {
      task: null,
    };
  },
  methods: {
    addTask() {
      if (this.task != null) {
        this.$emit('add-task',this.task);
        this.task = null;
      }
    },
  },
};
</script>

<style scoped>
button {
  background: #13e328;
  width: 44px;
  height: 44px;
  cursor: pointer;
}
input {
  border: 1px solid #e1e1e1;
  background: #ffffff;
  width: 100%;
  height: 40px;
}
.field {
  display: flex;
  /* justify-content: center; */
  margin-bottom: 15px;
  width: 100%;
}
</style>
