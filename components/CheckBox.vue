<template>
  <input type="checkbox" @change="updateValue" :checked="checked" />
</template>

<script>
export default {
  model: {
    prop: "checked",
    event: "change",
  },
  props: {
    checked: {
      type: Boolean,
      required: true,
    },
  },
  setup(_, context) {
    const updateValue = (e) => {
      context.emit("update:change", e.target.checked);
    };
    return { updateValue };
  },
};
</script>

<style scoped></style>
