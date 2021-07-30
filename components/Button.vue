<template>
  <button class="button" @click="push">
    {{ this.msg }}
  </button>
</template>

<script>
export default {
  props: ["msg"],
  methods: {
    push() {
      this.$emit("push");
    },
  },
};
</script>

<style scoped>
.button {
  font-size: 1em;
  background-color: #71ff71;
  color: #fff;
  border-style: none;
}

.button:disabled {
  background: #efefef;
  opacity: 0.8;
}
</style>
