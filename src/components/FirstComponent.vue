<script>
export default {
  name: 'FirstComponent',

  props: {
    value: {
      required: false,
      type: String,
      default: ""
    },
    km: {
      required: false,
      type: Number,
      default: null,
    }
  }
}
</script>

<template>
  <div>
    {{ km }}
    <input :value="value" @input="$emit('input', $event.target.value)  ">
  </div>
</template>

<style>
  input{
    margin-top: 10px;
  }
</style>