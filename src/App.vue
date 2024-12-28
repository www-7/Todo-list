<template>
  <main>
    <div class="conteiner">
      <div class="field">
        <input
          type="text"
          v-model="text" />
        <button @click="addTodo">
          <img
            src="./assets/Vector.png"
            alt="" />
        </button>
      </div>
      <my-button-block></my-button-block>
      <MyTodoList
        v-if="item in arrTodo"
        :key="item"
        :title="item" />
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
        text: '',
        arrTodo: []
      };
    },
    methods: {
      addTodo() {
        if(this.text !== '') {
          this.arrTodo.push(this.text)
        }
        
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
    background: #13e328;
    border: none;
    width: 44px;
    height: 44px;
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
