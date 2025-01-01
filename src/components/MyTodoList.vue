<template>
  <div class="todo">
    <div class="list">
      <input
        v-model="checkedValue"
        class="checkeds"
        type="checkbox"
        :id="id" />
      <label
        v-if="edit"
        :class="checked ? 'text_decoration' : 'text'"
        :for="id"
        >{{ textValue }}</label
      >
      <input
        v-if="!edit"
        type="text"
        v-model.trim="textValue" />
    </div>
    <div class="btn_block">
      <button
        v-if="edit"
        @click="edit = !edit"
        class="edit btn">
        <img
          
          src="/src/assets/Pencil.png"
          alt="edit" />
      </button>
      <button
        v-if="!edit"
        @click="edit = !edit"
        class="active btn">
        <img
          
          src="/src/assets/check.png"
          alt="edit" />
      </button>
      <button
        @click="$emit('delete')"
        class="delete btn">
        <img
          
          src="/src/assets/delete.png"
          alt="delete" />
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      text: {
        type: String,
        require: true,
      },
      checked: {
        type: Boolean,
        require: true,
      },
      id: {
        type: Number,
        require: true,
      },
    },
    emits: ['delete', 'text', 'checked'],
    data() {
      return {
        edit: true,
      };
    },
    computed: {
      textValue: {
        get() {
          return this.text;
        },
        set(value) {
          this.$emit('update:text', value);
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
  .btn_block {
    display: flex;
    /* align-items: center;
    justify-content: center; */
    /* gap: 10px; */
  }
  .edit {
    background: #0085ff;
  }
  .active {
    background: #00ba00;
  }
  .delete {
    background: #ff0000;
  }
  .btn {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-right: 10px;
    width: 20px;
    height: 20px;
    border-radius: 5px;
    border: none;
    cursor: pointer;
  }
  .text_decoration {
    text-decoration: line-through;
    text-transform: capitalize;
  }
  .text {
    text-transform: capitalize;
  }
  /* .displayed {
    display: flex;
    align-items: center;
    justify-content: center;
  } */
  /* #00BA00 */
</style>
