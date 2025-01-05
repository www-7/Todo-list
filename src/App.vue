<template>
  <main>
    <test v-model="text"></test>
    <div class="conteiner">
      <h2>Список задач {{ $store.state.test }}</h2>
      <input-task @add-task="addTask"></input-task>
      <button-block v-model="filters"></button-block>
      <!-- <component :is="myButtonBlock"></component> -->
      <item-task
        v-for="item in visibleItems"
        :key="item.id"
        :id="item.id"
        v-model:note="item.note"
        v-model:checked="item.checked"
        @delete="deleteTask(item.id)"
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
    // Test,
    InputTask,
    ButtonBlock,
    ItemTask,
  },

  data() {
    return {
      text: 'test',
      arrTodo: [],
      filters: 'all', // 'all' 'completed' 'pending'
    };
  },
  // provide() {
  //   return {
  //     test: computed(() => this.testes.text)
  //   }
  // },
  computed: {
    visibleItems() {
      if (this.filters === 'all') {
        return this.arrTodo;
      }
      if (this.filters === 'completed') {
        return this.arrTodo.filter((i) => i.checked === true);
      }
      if (this.filters === 'pending') {
        return this.arrTodo.filter((i) => i.checked === false);
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
        checked: false,
      });
    },
    deleteTask(id) {
      this.arrTodo = this.arrTodo.filter((i) => i.id !== id);
    },
    generateId() {
      return Math.random().toString(16).substring(2);
    },
    // checkbox() {
    // return
    // }
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
.field {
  display: flex;
  margin-bottom: 15px;
  width: 100%;
}
</style>
