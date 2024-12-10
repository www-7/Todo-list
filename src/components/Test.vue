<template>
  <div>
    <div>number: {{ number }}</div>
    <div>modelValue: {{ modelValue }}</div>
    <input v-model="value" />
  </div>
</template>

<script>
export default {
  name: 'Test',
  props: {
    modelValue: {
      type: String,
    },
  },
  data() {
    return {
      number: 1,
    };
  },
  computed: {
    value: {
      get() {
        return this.modelValue;
      },
      set(v) {
        console.log('set', v);
        this.$emit('update:modelValue', v);
      },
    },
  },
};
</script>
