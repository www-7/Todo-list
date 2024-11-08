<template>
  <div class="btn-menu">
    <button class="btn">All</button>
    <button class="btn">Complated</button>
    <button class="btn">Pending</button>
  </div>
</template>

<script>
export default {
    data() {
        return {

        }
    }
}
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
    
  }
  .btn:hover {
    background: #8f8f8f;
    color: #FFFFFF;

  }
  btn:last-child {
    margin-right: 0;
  }
</style>
