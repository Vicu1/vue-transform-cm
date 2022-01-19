<script>
import FirstComponent from '@/components/FirstComponent.vue';
import Modal from '@/components/Modal.vue';

export default {
  name: "App",

  components: {
    FirstComponent,
    Modal
  },

  data: () => ({
    show: false,
    kilometers: false,
    opened: false,
    model: {
      cm: '12321',
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
      this.show = true;
      this.$nextTick(() => {
        this.$refs.input.focus();
      })
  },

  methods: {
    openDialog() {
      this.opened = true;
    }
  }
};
</script>


<template>
  <div id="app">
    <input ref="input" type="text" v-model="model.cm" v-if="show"  placeholder="cm">
    <input :value="meters" v-if="show" type="text" placeholder="m">
    <input :value="km" v-if="kilometers && show" type="text" placeholder="km">
    <first-component :km="km" v-model="model.cm" />
    <modal v-model="opened">
      <template #button>
        <button>
          close
        </button>
      </template>
    </modal>
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
