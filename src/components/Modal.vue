<script>
export default {
  name: "Modal",

  props: {
    value: {
      required: true,
      type: Boolean
    }
  },

  data: () => ({
    model: false
  }),

  watch: {
    value: {
      handler() {
        this.model = this.value;
      },

      immediate: true,
    }
  },

  methods: {
    close() {
      this.model = false;
      this.$emit("input", this.model);
    },
    openModal() {
      this.model = true;
    }
  }
}
</script>

<template>
  <div>
    <slot name="button" :activator="openModal"></slot>
    <div class="modalDialog" v-if="model">
      <button class="close" @click="close()">
        <img src="../assets/close.png" alt="close">
      </button>
    </div>
  </div>
</template>

<style scoped>
  .close {
    background: transparent;
    border: none;
    cursor: pointer;
    position: absolute;
    top: 0;
    right: 0;
  }

  .modalDialog {
    position: absolute;
    width: 400px;
    height: 400px;
    background-color: black;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 2;
  }
</style>