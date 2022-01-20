<script>

export default {
  name: "Tabs-item",

  props: {
    item: {
      required: true,
      type: Number,
    }
  },

  data: () => ({
    tabsContent: [... new Array(25)].map((item,index) => `content ${index}`),
  }),
}
</script>

<template>
  <div>
    <ul>
      <li>
        {{ tabsContent[item] }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul{
  list-style: none;
  text-align: center;
}

</style>
