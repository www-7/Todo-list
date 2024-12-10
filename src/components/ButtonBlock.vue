<template>
  <div class="btn-menu">
    <button
      class="btn"
      @click="$emit('update:model-value', 'all')"
    >
      All
    </button>
    <button
      class="btn"
      @click="$emit('update:modelValue', 'completed')"
    >
      Complated
    </button>
    <button
      class="btn"
      @click="$emit('update:modelValue', 'pending')"
    >
      Pending
    </button>
  </div>
  <!-- <p>{{ $store.state.test }}</p> -->
</template>

<script>
export default {
  data() {
    return {
      active: '',
    };
  },
};
</script>

<style scoped>
.btn-menu {
  display: flex;
  justify-content: space-between;
  width: 390px;
  margin-bottom: 15px;
}
.btn {
  /* margin-right: 10px; */
  width: 124px;
  right: 30px;
  border: 1px solid #cfcfcf;
  border-radius: 6px;
  font-family: Nunito;
  font-size: 14px;
  font-weight: 700;
  line-height: 19.1px;
  text-align: center;
  cursor: pointer;
}
.btn:hover {
  background: #8f8f8f;
  color: #ffffff;
}
btn:last-child {
  margin-right: 0;
}
</style>
