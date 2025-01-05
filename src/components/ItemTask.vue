<template>
  <div class="todo">
    <div class="list">
      <input
        type="checkbox"
        :id="id"
        v-model="checkedValue"
      />
      <label
        v-if="edit"
        :class="checked? 'text_decoration' : 'text'"
        :for="id"
        >{{ noteValue }}</label
      >
      <input
        v-if="!edit"
        type="text"
        v-model.trim="noteValue"
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
import focusDirective from './focusDirective';
export default {
  // setup() {
  //   const inputEdit = ref()
  //   onMounted(() => inputEdit.value.focus())
  //   return [inputEdit]
  // },
  props: {
    note: {
      type: String,
    },
    checked: {
      type: Boolean,
    },
    id: {
      type: String,
    },
  },
  computed: {
    noteValue: {
      get() {
        return this.note;
      },
      set(value) {
        this.$emit('update:note', value);
      },
    },
    checkedValue: {
      get() {
        return this.checked;
      },
      set(value) {
        this.$emit('update:checked', value);
      },
    },
  },
  // inject: ['test'],
  emits: ['update:note', 'update:checked', 'delete'],
  directives: focusDirective,
  data() {
    return {
      edit: true,
      // checked: false,
    };
  },
  methods: {
    // checkbox() {
    //   this.$emit('checkbox', this.checked);
    // },
  },
};
</script>

<style scoped>
.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
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
.text {
  text-transform: capitalize;
}
.text_decoration {
  text-decoration: line-through;
  text-transform: capitalize;
}
</style>
