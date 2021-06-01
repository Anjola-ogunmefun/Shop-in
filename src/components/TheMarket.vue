<template>
  <div class="container">
    <div class="row">
      <section>
        <list-items
          v-for="item in items"
          :key="item.id"
          :id="item.id"
          :name="item.name"
          :description="item.description"
          :price="item.price"
          :url="item.url"
          @cart-content="showInCart"
        ></list-items>
      </section>
    </div>
  </div>
</template>

<script>
import ListItems from "./ListItems.vue";
export default {
  components: {
    ListItems,
  },
  inject: ["items", "myCart", "totalCost", "sumTotal"],

  methods: {
    showInCart(name, itemQuantity, value, id, url) {
      const addedItem = {
        name: name,
        itemQuantity: itemQuantity,
        value: value,
        id: id,
        url: url,
      };
      this.myCart.push(addedItem);
      console.log(this.myCart);
      this.totalCost.push(addedItem.value);
      const reducer = (accumulator, currentValue) => accumulator + currentValue;
      this.sumTotal = this.totalCost.reduce(reducer);
      console.log("total", this.sumTotal);
    },
  },
};
</script>

<style scoped>
section {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-auto-rows: auto;
  grid-gap: 0.75rem;
}
</style>
