<template>
  <section>
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <div class="card h-100 border-secondary" style="width:25rem">
            <img
              :src="url"
              class="card-img-top"
              style="padding:1rem;height:250px"
              alt="product image"
            />
            <div class="card-body">
              <h2 class="card-title">{{ name }}</h2>
              <!-- <h4 class="card-text">
                {{ description }}
              </h4> -->
              <div class="quantity">
                <h5>Quantity</h5>
                {{ itemQuantity }}
              </div>
              <p class="quantity">
                Cost:
                <span style="background-color:transparent; margin:0"
                  >&#8358;</span
                >{{ value.toLocaleString() }}
              </p>
              <button
                class="btn btn-danger"
                @click="$emit('remove-product', id)"
              >
                Remove Item
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
    },
    name: {
      type: String,
    },
    itemQuantity: {
      type: Number,
    },
    value: {
      type: Number,
    },
    url: {
      type: String,
    },
    sumTotal:{
      type:Number
    }
  },
};
</script>

<style scoped>
section {
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
  /* display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  grid-gap: 1rem; */
}
.quantity {
  font-size: 16px;
  margin-top: 20px;
}
</style>
