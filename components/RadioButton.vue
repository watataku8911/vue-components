<template>
  <div>
    <label v-for="(option, index) in options" :key="index">
      <!-- ラジオボタンにはname属性必須 -->
      <input
        type="radio"
        :value="option.value"
        @change="updateValue"
        name="radio-button"
      />{{ option.label }}</label
    >
  </div>
</template>

<script>
export default {
  props: {
    options: { type: Array, required: true },
  },
  emits: ["update:modalValue"],
  setup(_, context) {
    const updateValue = (e) => {
      context.emit("update:modalValue", e.target.value);
    };
    return { updateValue };
  },
};
</script>
<style scoped>
div {
  border: solid;
  display: flex;
  justify-content: space-around;
}
</style>
