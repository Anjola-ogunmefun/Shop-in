<template>
  <section>
    <the-header></the-header>

    <base-button>
      <li
        class="nav-item mr-2"
        @click="changeSelectedTab('the-market')"
      >
        <a class="btn btn-outline-danger btn-lg">List item</a>
      </li>
      <li
        class="nav-item"
        @click="changeSelectedTab('my-cart')"
      >
        <a class="btn btn-outline-danger btn-lg">My cart</a>
      </li>
    </base-button>

    <keep-alive>
      <component :is="selectedTab"></component>
    </keep-alive>
  </section>
</template>

<script>
export default {
  props: ["something"],
  data() {
    return {
      totalCost: [],
      value: 0,
      myCart: [],
      sumTotal: 0,
      selectedTab: "the-market",

      allItems: [
        {
          id: 1,
          name: "Mama's Pride rice",
          description: "5kg mini bag of rice; clean, fortified with vitamins",
          price: 5570,
          url: "https://foodstuffmarket.com/wp-content/uploads/2015/04/mama-pride-rice-foodstuffmarket-3.png",
        },
        {
          id: 2,
          name: "Gullon mini Crackers",
          description:
            "Delicious, filling and nutritious. You will not stop at one",
          price: 1500,
          url: "https://cdn.shopify.com/s/files/1/0322/5894/9164/products/9781BBB51CF6B0FD263F226D50597148_1024x1024.jpg?v=1582241395",
        },
        {
          id: 3,
          name: "molfix wipes",
          description:
            "sanitary with a lovely frgarnce, smooth and gentle on the skin",
          price: 500,
          url: "https://monmartt.com/img/products/8/8c9aecdaaa71ef621fb78f84a9a19ed2.png",
        },
        {
          id: 4,
          name: "Johnnie walker -Black Label",
          description: "Blended scotch whiskey",
          price: 7500,
          url: "https://www-konga-com-res.cloudinary.com/w_auto,f_auto,fl_lossy,dpr_auto,q_auto/media/catalog/product/N/C/171122_1589283385.jpg",
        },
        {
          id: 5,
          name: "Dior book tote",
          description: "Designer Dior bag",
          price: 500000,
          url: "https://wwws.dior.com/couture/ecommerce/media/catalog/product/cache/1/cover_image_mobile_1/715x773/17f82f742ffe127f42dca9de82fb58b1/w/5/1604954704_M1286ZRIW_M928_E01_GHC.jpg",
        },
         {
          id: 6,
          name: "iPhone X",
          description: "apple iPhone 10(X)- Black",
          price: 450000,
          url: "https://fdn2.gsmarena.com/vv/bigpic/apple-iphone-x.jpg",
        },
          {
          id: 7,
          name: "Maltina",
          description: "Maltina soft drink- A pack of 24",
          price: 3400,
          url: "https://i0.wp.com/www.drinks.ng/wp-content/uploads/2021/02/3b797808f261cedbbd9af1db5e8f6e7b823ef50a.png?fit=250%2C250&ssl=1",
        },
          {
          id: 8,
          name: "Nescafe Gold- expresso",
          description: "Italian style, Rich with Crema",
          price: 3000,
          url:"https://ga1.us-fx.dev/media/catalog/product/cache/e4d64343b1bc593f1c5348fe05efa4a6/n/e/ne003-2.jpg",
        },
         {
          id: 9,
          name: "Oxford Cabin Biscuit",
          description: "Classic snack you would enjoy",
          price: 300,
          url: "https://www-konga-com-res.cloudinary.com/w_auto,f_auto,fl_lossy,dpr_auto,q_auto/media/catalog/product/L/X/174946_1595489059.jpg",
        },
         {
          id: 10,
          name: "Nivea Deodorant- pack of 6",
          description: "Freshness all day long",
          price: 4000,
          url: "https://www-konga-com-res.cloudinary.com/w_auto,f_auto,fl_lossy,dpr_auto,q_auto/media/catalog/product/O/G/171328_1588930034.jpg",
        },
      ],
    };
  },
  // computed: {
  //   marketTab() {
  //     if (this.selectedTab === "the-market") {
  //       return "active";
  //     }
  //     return null;
  //   },
  //   cartTab() {
  //     return this.selectedTab === "my-cart" ? "active" : null;
  //   },
  // },
  methods: {
    changeSelectedTab(component) {
      this.selectedTab = component;
    },
  },

  provide() {
    return {
      items: this.allItems,
      totalCost: this.totalCost,
      value: this.value,
      myCart: this.myCart,
      sumTotal: this.sumTotal,
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Jost&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: monospace;
}

body {
  margin: 0;
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
}

a {
  /* color:black !important; */
  cursor: pointer;
  font-size: 2rem;
  margin: 0 1rem;
}
</style>
