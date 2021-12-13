<template>
  <select :name="name" @input="updateValue">
    <option value="0">選択してください</option>
    <option
      v-for="(option, index) in options"
      :key="index"
      :value="option.value"
    >
      {{ option.label }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    name: { type: String, required: true },
    options: { type: Array, required: true },
  },
  emits: ["update:select"],
  setup(_, context) {
    const updateValue = (e) => {
      context.emit("update:select", e.target.value);
    };
    return { updateValue };
  },
};
</script>
