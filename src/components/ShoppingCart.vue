<template>
  <div id="app">
    <div class="cart">
      <div v-for="(item, index) in items" :key="index" class="cart-item">
        <img :src="item.image" alt="Product Image" class="product-image" />
        <div class="product-details">
          <h3 class="product-title">{{ item.title }}</h3>
          <p class="product-description">{{ item.description }}</p>
          <p class="product-price">{{ item.price }}{{ kr }}</p>
          <div class="product-quantity">
            <button
              @click="decrementItem(index)"
              class="btn btn-outline-secondary"
              id="btn btn-outline-secondary"
            >
              -
            </button>
            <span class="quantity">{{ item.quantity }}</span>
            <button
              @click="incrementItem(index)"
              class="btn btn-outline-secondary"
              id="btn btn-outline-secondary"
            >
              +
            </button>
          </div>
          <button @click="deleteItem(index)" class="btn btn-danger">
            Delete
          </button>

          <!-- Extra -->
          <!-- <div class="cart-del">
          <button @click="showConfirm = true">Delete</button>
          <div v-if="showConfirm" class="container">
          <div class="content" >
        
          <div class="contentConf">
            <p2>Are you sure want to delete this item ?</p2>
            <br>
          <button @click="deletItem" class="BTN">confirm</button>
          <button @click="showConfirm = false" class="BTN">cancel</button>
          </div>
          </div>
          </div>
          </div> -->
          <!--  -->
        </div>
      </div>
      <div class="cart-total">
        <h2 class="total">Total: {{ getTotalPrice }}{{ kr }}</h2>
        <button @click="buy = !buy" class="buyBtn">Buy</button>
        <div class="showMsg">
          <h3 v-if="buy" class="show">{{ text }}{{ getTotalPrice }}{{ kr }}</h3>
          <h3 v-if="buy" class="show">Thank you for your shopping!</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 2 Extra
      // showConfirm: false,
      // deletItem: true,
      buy: false,
      text: "Total Receipt Amount :    ",
      kr: "  Kr",

      items: [
        {
          title: "PECKSNIFFS CANDLE",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: "src/assets/img/img6.webp",
          price: 299,
          quantity: 1,
        },
        {
          title: "SCENTED CANDLE",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: "src/assets/img/img9.webp",
          price: 399,
          quantity: 1,
        },
        {
          title: "CORINESS CANDLE",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: "src/assets/img/img10.webp",
          price: 199,
          quantity: 1,
        },
      ],

      //  EXTRA
      // props: {
      //   message: {
      //     type: String,
      //     required: true,

      //     // showConfirm:false,
      //     // deletItem:true,
      //   },
      // },
      // methods: {
      //   showConfirm() {
      //     this.$emit("cancel");
      //   },
      //   deletItem() {
      //     this.items.splice(index, 1);
      //   },
      // },
    };
  },

  // END EXTRA

  methods: {
    incrementItem(index) {
      this.items[index].quantity++;
    },
    decrementItem(index) {
      if (this.items[index].quantity > 1) {
        this.items[index].quantity--;
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
      if (confirm("Are you sure to remove the item ?")) {
      }
    },
  },
  computed: {
    getTotalPrice() {
      return this.items.reduce(
        (total, item) => total + item.price * item.quantity,
        0
      );
    },
  },
};
</script>

<style>
div #app {
  margin-top: -50px;
}
.cart {
  margin: 0 auto;
  width: 80%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.cart-item {
  display: flex;
  margin: 10px;
  border: 1px solid rgb(168, 102, 57);

  padding: 10px;
  width: 100%;
}

.product-image {
  max-width: 150px;
  margin-right: 10px;
}

.product-details {
  display: flex;
  flex-direction: column;
}

.product-title {
  margin: 0 0 10px 0;
}

.buyBtn {
  background-color: rgb(253, 242, 204);
  border-radius: 5px;
  width: 100px;
  padding: 2px;
  margin: auto;
}

.show,
.total,
.buyBtn {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
}

.product-description {
  margin: 0 0 10px 0;
}

button[class="btn btn-danger"] {
  width: 60px;
  font-size: 12px;
  font-weight: 600;
  margin-left: 800px;
  background-color: rgb(206, 128, 76);
  border: none;
}

button[class="btn btn-danger"]:hover {
  background-color: rgb(199, 131, 85);
}

button[class="btn btn-outline-secondary"],
[class="btn btn-outline-secondary"] {
  background-color: rgb(168, 102, 57);
  color: white;
  /* border-radius: 80px; */
  border: none;
}

button[id="btn btn-outline-secondary"] {
  width: 34px;
}

.cart-total {
  font-size: 30px;
  font-weight: 600;
}

button[class="btn btn-outline-secondary"]:hover {
  background-color: rgb(199, 131, 85);
}

/* EXTRA */

.content {
  background-color: white;
  padding: 1em;
  border-radius: 0.5em;
  text-align: center;
}

.contentConf {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 1em;
}

@media screen and (min-width: 360px) and (max-width: 980px) {
  .show {
    font-size: 18px;
  }

  .buyBtn {
    height: 35px;
    width: 60px;
    font-size: 20px;
  }

  .total {
    font-size: 18px;
    font-weight: 700;
  }

  button[class="btn btn-danger"] {
    margin-left: 5px;
  }

  h3[class="product-title"] {
    font-size: 15px;
    font-weight: 700;
  }

  p[class="product-description"] {
    font-size: 12px;
  }
  button[id="btn btn-outline-secondary"] {
    margin-bottom: 10px;
    width: 30px;
    height: 30px;
  }
}
</style>
