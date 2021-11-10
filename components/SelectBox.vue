<template>
  <select :name="this.name" @input="updateValue" :select="this.select">
    <option value="0">選択してください</option>
    <option
      v-for="(option, index) in this.options"
      :key="index"
      :value="option.value"
      >{{ option.label }}</option
    >
  </select>
</template>

<script>
export default {
  props: {
    select: { type: Number, required: true },
    name: { type: String, required: true },
    options: { type: Array, required: true },
  },
  methods: {
    updateValue(e) {
      this.$emit("input", e.target.value);
    },
  },
};
</script>
