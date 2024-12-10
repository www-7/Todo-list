<template>
  <div class="todo">
    <div class="list">
      <input
        type="checkbox"
        v-model="checked"
      />
      <label class="text" for="item.id">{{ modelValue }}</label>
      <input
        type="text"
        v-if="edit"
        v-model.trim="value"
        v-focus
      />
    </div>
    <div>
      <button
        @click="edit = !edit"
        class="edit btn"
      >
        <img
          src="/src/assets/Pencil.png"
          alt=""
        />
      </button>
      <button
        @click="$emit('delete')"
        class="delete btn"
      >
        <img
          src="/src/assets/delete.png"
          alt=""
        />
      </button>
    </div>
  </div>
</template>

<script>
// import { onMounted, ref } from 'vue';

export default {
  // setup() {
  //   const inputEdit = ref()
  //   onMounted(() => inputEdit.value.focus())
  //   return [inputEdit]
  // },
  props: {
    modelValue: {
      type: String
    },
  },
  computed: {
    value: {
      get() {
        return this.modelValue
      },
      set(value) {
        this.$emit('update:modelValue', value)
      }
    }
  },
  // inject: ['test'],
  emits: {
    delete() {},
  },
  data() {
    return {
      edit: false,
      checked: false
    };
  },
  methods: {
    
  },
};
</script>

<style scoped>
.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 390px;
  height: 40px;
  border: 1px solid #e1e1e1;
}
.edit {
  background: #0085ff;
}
.delete {
  background: #ff0000;
}
.btn {
  margin-right: 10px;
  width: 20px;
  height: 20px;
  border-radius: 5px;
  cursor: pointer;
}
</style>
