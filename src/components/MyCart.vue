<template>
  <section>
    <div class="container">
      <div class="row">
        <h1 class="display-4">My cart</h1>
        <hr />
        <p v-if="myCart.length === 0" class="display-5">Cart is Empty!</p>

        <cart-structure
          v-else
          v-for="product in myCart"
          :key="product.id"
          :id="product.id"
          :name="product.name"
          :value="product.value"
          :itemQuantity="product.itemQuantity"
          :url="product.url"
          @remove-product="deleteItem"
        >
        </cart-structure>

        <p v-if="sourceControl" class="display-6">Total: <span>&#8358;</span>{{ sumTotal.toLocaleString() }}</p>
        <p v-else class="display-6">Total:<span>&#8358;</span> {{ sumTotal.toLocaleString() }}</p>

        <button class="btn btn-warning btn-lg" :disabled="isActive">
          Check out
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  inject: ["myCart", "sumTotal", "totalCost"],

  data() {
    return {
      sumSource: "market",
    };
  },
  computed: {
    isActive() {
      return this.myCart.length === 0 ? true : false;
    },
    sourceControl() {
      return this.sumSource === "market" ? this.sumUp() : null;
    },
  },
  methods: {
    deleteItem(itemId) {
      const itemToDelete = this.myCart.find((item) => itemId === item.id);
      const indexOfItem = this.myCart.indexOf(itemToDelete);
      this.myCart.splice(indexOfItem, 1);
      console.log(itemToDelete);

      if (this.totalCost.length > 1) {
        this.totalCost.pop(itemToDelete.value);
        const reducer = (accumulator, currentValue) =>
          accumulator - currentValue;
        this.sumTotal = this.totalCost.reduce(reducer);
        console.log("total", this.sumTotal);
      } else {
        this.sumTotal = 0;
      }
    },

    sumUp() {
      if (this.totalCost.length === 1) {
        this.sumTotal = this.totalCost[0];
      } else if (this.totalCost.length > 1) {
        const reducer = (accumulator, currentValue) =>
          accumulator + currentValue;
        this.sumTotal = this.totalCost.reduce(reducer);
      } else {
        this.sumTotal = 0;
      }
    },
  },
};
</script>

<style scoped>
section {
  margin: 1rem auto;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-auto-rows: auto;
  grid-gap: 0.75rem;
}
p {
  margin-top: 100px;
}

button {
  margin-top: 30px;
  margin-left: -10px;
}
</style>
