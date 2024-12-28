<template>
  <main>
    <div class="conteiner">
      <input-field @add-todo="addTodo"></input-field>

      <my-button-block v-model="filter" />
      <my-todo-list
        v-for="item in visibleItems"
        :key="item.id"
        :id="item.id"
        v-model:text="item.text"
        v-model:checked="item.checked"
        @delete="deleteTodo(item.id)" />
    </div>
  </main>
</template>

<script>
  import InputField from './components/InputField.vue';
  import MyButtonBlock from './components/MyButtonBlock.vue';
  import MyTodoList from './components/MyTodoList.vue';
  export default {
    components: {
      InputField,
      MyButtonBlock,
      MyTodoList,
    },
    data() {
      return {
        filter: 'all',
        arrTodo: [],
        id: 0
      };
    },
    created() {
      this.arrTodo = JSON.parse(localStorage.getItem('arrTodo')) || [];
    },
    computed: {
      visibleItems() {
        if (this.filter === 'all') {
          return this.arrTodo;
        }
        if (this.filter === 'complated') {
          return this.arrTodo.filter((i) => i.checked === true);
        }
        if (this.filter === 'pending') {
          return this.arrTodo.filter((i) => i.checked === false);
        }
      },
    },
    methods: {
      addTodo(text) {
        this.arrTodo.push({
          text: text,
          id: this.generateId(),
          checked: false,
        });
      },
      deleteTodo(id) {
        this.arrTodo = this.arrTodo.filter((i) => i.id !== id);
      },
      generateId() {
        // return Math.random().toString(16).substring(2);
        return this.id++
      },
      editTodo() {},
    },
    watch: {
      arrTodo: {
        handler(newValue) {
          localStorage.setItem('arrTodo', JSON.stringify(newValue));
        },
        deep: true,
        imediate: false,
      },
    },
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
