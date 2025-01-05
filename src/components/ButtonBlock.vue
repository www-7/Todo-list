<template>
  <div class="btn-menu">
    <button
      class="btn"
      :class="{ 'btn--active': modelValue === 'all' }"
      @click="clickAll"
    >
      All
    </button>
    <button
      class="btn"
      :class="{ 'btn--active': modelValue === 'Complated' }"
      @click="clickCompleted"
    >
      Complated
    </button>
    <button
      class="btn"
      :class="{ 'btn--active': modelValue === 'Pending' }"
      @click="clickPending"
    >
      Pending
    </button>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: {
      type: String
    }
  },
  data() {
    return {
    };
  },
  methods: {
    clickAll() {
      this.$emit('update:model-value', 'all');
    },
    clickCompleted() {
      this.$emit('update:modelValue', 'completed');
    },
    clickPending() {
      this.$emit('update:modelValue', 'pending');
    },
  },
};
</script>

<style scoped>
.btn-menu {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  width: 100%;
  margin-bottom: 15px;
}
.btn--active {
  background: #8f8f8f;
  color: #ffffff;
}
.btn {
  width:100%;
  height: 25px;
  border: 1px solid #cfcfcf;
  border-radius: 6px;
  font-family: Nunito;
  font-size: 14px;
  font-weight: 700;
  line-height: 19.1px;
  text-align: center;
  cursor: pointer;
}

/* btn:last-child {
  margin-right: 0;
} */
</style>
