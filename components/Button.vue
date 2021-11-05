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
  border-radius: 10px;
  padding: 1%;
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
