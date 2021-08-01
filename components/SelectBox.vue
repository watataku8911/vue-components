<template>
  <select name="select-box" @input="updateValue">
    <option value="0">選択してください</option>
    <option
      v-for="(option, index) in options"
      :key="index"
      :value="option.value"
      >{{ option.label }}</option
    >
  </select>
</template>

<script>
export default {
  props: {
    options: { type: Array, required: true },
  },
  methods: {
    updateValue(e) {
      this.$emit("input", e.target.value);
    },
  },
};
</script>

<style>
select {
  text-align: center;
  display: block;
}
</style>
