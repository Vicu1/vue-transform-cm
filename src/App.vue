<script>

export default {
  name: "App",

  data: () => ({
    show: false,
    kilometers: false,
    model: {
      cm: '1000000',
      meter: '',
    }
  }),

  computed: {
    meters() {
      return this.model.cm / 100;
    },
    km() {
      return this.model.cm / 100000;
    },
  },

  watch: {
    model: {
      immediate: true,
      deep: true,
      handler() {
        if (this.model.cm >= 10000) {
          this.kilometers = true;
        } else {
          this.kilometers = false;
        }
      }
    }
  },

  mounted() {
    setTimeout(() => {
      this.show = true;
      this.$nextTick(() => {
        this.$refs.input.focus();
      })
    },1000);
  },
};
</script>


<template>
  <div id="app">
    <input ref="input" v-model="model.cm" v-if="show" type="text" placeholder="cm">
    <input :value="meters" v-if="show" type="text" placeholder="m">
    <input :value="km" v-if="kilometers && show" type="text" placeholder="km">
  </div>
</template>


<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
