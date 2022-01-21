<script>
export default {
  name: 'Table',

  data: () => ({
    value_title: '',
    value_price: '',
    tableItems: [
      {title: 'Bread', price: 2 , },
      {title: 'Milk', price: 4 , },
      {title: 'Snickers', price: 6 , }

    ],
  }),

  computed: {
    total() {
      return this.tableItems.reduce((acc, item) => acc + item.price, 0);
    }
  },

  methods: {
    addItem() {
      if (this.value_title && this.value_price){
        this.tableItems.push({title: this.value_title, price: Number(this.value_price)});
        this.value_title = '';
        this.value_price = '';
      }
    },
    removeItem(index) {
      this.tableItems.splice(index, 1);
    },
  }
}

</script>

<template>
  <div>
    <input v-model="value_title" placeholder="Name" type="text">
    <input v-model="value_price" placeholder="Price ($)" type="number">
    <button @click="addItem()">
      Add Item
    </button>
    <div class="table">
      <div class="table-row">
        <h2>
          Name
        </h2>
        <h2>
          Price
        </h2>
      </div>
      <div v-for="(item, index) of tableItems" :key="index" class="table-row">
        <h4>
          {{ item.title }}
        </h4>
        <h4>
          {{ item.price }}
        </h4>
        <button @click="removeItem(index)">
          x
        </button>
      </div>
      <div class="table-row">
        <h2>Total</h2>
        <h2>{{total}}</h2>
      </div>
    </div>
  </div>
</template>

<style scoped>
div {
  text-align: center;
}

.table {
  margin: 20px auto 0;
  max-width: 1000px;
  border: 2px solid black;

}

.table-row {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

</style>