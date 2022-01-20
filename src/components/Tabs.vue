<script>
import TabsItem from "@/components/Tabs-item";

export default {
  name: "Tabs",

  components: {
    TabsItem
  },

  data: () => ({
    tabsTitle: [...new Array(25)],
    activeTab: 0
  }),

  methods: {
    activateTab(index) {
      this.activeTab = index;
    }
  }
}
</script>

<template>
  <div>
    <ul>
      <li v-for="(item, index) of tabsTitle" :key="item" class="active" @click="activateTab(index)">Tab1</li>
    </ul>
    <tabsItem :item="activeTab" />
  </div>

</template>

<style scoped>
  ul{
    list-style: none;
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
  }
  li{
    cursor: pointer;
  }
</style>