<template>
  <div class="chip">
    {{ msg }}
  </div>
</template>

<script>
export default {
  props: {
    msg: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.chip {
  position: relative;
  top: -1.5vh;
  height: 32px;
  font-size: 1em;
  font-weight: 500;
  color: rgba(0, 0, 0, 0.6);
  line-height: 32px;
  padding: 0 15px;
  border-radius: 16px;
  background-color: #e4e4e4;
  margin-bottom: 5px;
  margin-right: 5px;
  display: inline-block;
  text-align: center;
}

.chip::before {
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  content: "";
  width: 0px;
  border-color: #e4e4e4;
  border-style: solid;
  border-width: 10px;
  border-left-color: transparent;
  border-bottom-color: transparent;
  border-right-color: transparent;
}
</style>
