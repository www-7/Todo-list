

<template>
  <main>
    <div class="conteiner">
      <div class="field">
        <input type="text" v-model="text">
        <button @click="addTodo"><img src="./assets/Vector.png" alt=""></button>
    </div>
      <my-button-block></my-button-block>
      <MyTodoList :title='addTodo()'/>
    </div>
  </main>
</template>

<script>
  import InputField from './components/InputField.vue';
  import MyButtonBlock from './components/MyButtonBlock.vue';
  import MyTodoList from './components/MyTodoList.vue'
  export default {
    components: {
      InputField,
      MyButtonBlock,
      MyTodoList,
    },
    data() {
      return {
        text: ''
      };
    },
    methods: {
      addTodo() {
        return this.text
      }
    }
  };
</script>

<style scoped>
  .conteiner {
    width: 25%;
    margin: 0 auto;
  }
  button {
    background: #13E328;
    border: none;
    width: 44px;
    height: 44px;
}
input {
    border: 1px solid #E1E1E1;
    background: #FFFFFF;
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
