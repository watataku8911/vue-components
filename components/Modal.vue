<template>
  <transition name="modal">
    <div class="overlay" @click="handleClose">
      <div class="panel" @click.stop>
        <h2>{{ title }}</h2>
        <div class="module--spacing--small"></div>
        <div class="modal-contents">
          <p>{{ detail }}</p>
        </div>
        <Button :disabled="false" msg="ボタン" @push="click" />
      </div>
    </div>
  </transition>
</template>

<script>
import Button from "./Button.vue";
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    detail: {
      type: String,
      required: true,
    },
  },
  components: {
    Button,
  },
  emits: ["close", "modal-click"],
  setup(_, context) {
    const handleClose = () => {
      context.emit("close");
    };
    const click = () => {
      context.emit("modal-click");
    };
    return { handleClose, click };
  },
};
</script>

<style scoped>
.overlay {
  background: rgba(0, 0, 0, 0.8);
  position: fixed;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  z-index: 900;
  transition: all 0.5s ease;
}

.panel {
  width: 40%;
  text-align: center;
  background: #fff;
  padding: 40px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.modal-contents {
  text-align: left;
}

.modal-enter,
.modal-leave-active {
  opacity: 0;
}

.modal-enter .panel,
.modal-leave-active .panel {
  top: -200px;
}
</style>
