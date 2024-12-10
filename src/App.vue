<template>
  <main>
    <test v-model="text"></test>
    <div class="conteiner">
      <h2>Список задач {{ $store.state.test }}</h2>
      <input-task @add-task="addTask"></input-task>
      <button-block v-model="filter"></button-block>
      <!-- <component :is="myButtonBlock"></component> -->
      <item-task
        v-for="item in visibleItems"
        :key="item.id"
        v-model="item.note"
        @delete="deleteTask(item.id)"
        @toogle-done="onToogleDone"
        @editTask="editTask"
      />
    </div>
  </main>
</template>

<script>
import { computed, onMounted, ref } from 'vue';
import InputTask from './components/InputTask.vue';
import ButtonBlock from './components/ButtonBlock.vue';
import ItemTask from './components/ItemTask.vue';
import Test from './components/Test.vue';
export default {
  components: {
    Test,
    InputTask,
    ButtonBlock,
    ItemTask,
  },
  data() {
    return {
      text: 'test',
      arrTodo: [],
      filter: 'all', // 'all' 'completed' 'pending'
    };
  },
  // provide() {
  //   return {
  //     test: computed(() => this.testes.text)
  //   }
  // },
  computed: {
    visibleItems() {
      if (this.filter === 'all') {
        return this.arrTodo;
      }
      if (this.filter === 'completed') {
        return this.arrTodo.filter((i) => i.checked === false);
      }
      if (this.filter === 'pending') {
        return this.arrTodo.filter((i) => i.checked === true);
      }
    },
  },
  created() {
    this.arrTodo = JSON.parse(localStorage.getItem('arrTodo')) || [];
  },
  methods: {
    addTask(task) {
      this.arrTodo.push({
        note: task,
        id: this.generateId(),
        checked: this.onToogleDone(),
      });
    },
    deleteTask(id) {
      this.arrTodo = this.arrTodo.filter((i) => i.id !== id);
    },
    generateId() {
      return Math.random().toString(16).substring(2);
    },
    newTask() {
      
    },
    onToogleDone() {
      
    },
  },
  watch: {
    arrTodo: {
      handler(newValue) {
        localStorage.setItem('arrTodo', JSON.stringify(newValue));
      },
      deep: true,
      immediate: false,
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
