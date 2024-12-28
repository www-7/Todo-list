<template>
  <div class="btn-menu">
    <button
      class="btn__click"
      @click="clickAll">
      Все
    </button>
    <button
      class="btn"
      @click="clickComplated">
      Выполнено
    </button>
    <button
      class="btn"
      @click="clickPending">
      В ожидании
    </button>
  </div>
  <!-- <button :class="{'btn':true, 'btn__сlick':!active}" @click="active = !active">btn</button> -->
</template>

<script>
  export default {
    data() {
      return {
        // clicked: true,
        // active: true
      };
    },
    methods: {
      clickAll() {
        this.$emit('update:modelValue', 'all')
      },
      clickComplated() {
        this.$emit('update:modelValue', 'complated')
      },
      clickPending() {
        this.$emit('update:modelValue', 'pending')
      }
    }
  };
</script>

<style scoped>
  .btn-menu {
    display: flex;
    justify-content: space-between;
    width: 390px;
    margin-bottom: 15px;
  }
  .btn__сlick {
    background: #8f8f8f;
    color: #ffffff;
    width: 124px;
    right: 30px;
    border: 1px solid #cfcfcf;
    border-radius: 6px;
    font-family: Nunito;
    font-size: 14px;
    font-weight: 700;
    line-height: 19.1px;
    text-align: center;
    cursor: pointer
  }
  .btn {
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
  btn:last-child {
    margin-right: 0;
  }
  
  
</style>
