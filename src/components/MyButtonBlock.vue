<template>
  <div class="btn-menu">
    <button
      class="btn"
      :class="{ 'btn--active': modelValue === 'all' }"
      @click="clickAll">
      Все
    </button>
    <button
      class="btn"
      :class="{ 'btn--active': modelValue === 'complated' }"
      @click="clickComplated">
      Выполнено
    </button>
    <button
      class="btn"
      :class="{ 'btn--active': modelValue === 'pending' }"
      @click="clickPending">
      В ожидании
    </button>
  </div>
  <!-- <button :class="{'btn':true, 'btn__сlick':!active}" @click="active = !active">btn</button> -->
</template>

<script>
  export default {
    props: {
      modelValue: {
        type: String,
      },
    },
    data() {
      return {
        // clicked: this.clickAll,
        // active: true
      };
    },
    methods: {
      clickAll() {
        this.$emit('update:modelValue', 'all');
      },
      clickComplated() {
        this.$emit('update:modelValue', 'complated');
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
    width: 100%;
    height: 25px;
    border: 1px solid #cfcfcf;
    border-radius: 6px;
    font-family: Nunito;
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
  }
</style>
