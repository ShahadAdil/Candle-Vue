<script setup>
import HeroImage from "../components/HeroImage.vue";
import CardsOffers from "../components/CardsOffers.vue";
</script>

<template>
  <HeroImage />
  <!-- <SearchImg/> -->
  <!-- <div class="search">
<h1>Search</h1>
<SearchImg></SearchImg>

</div> -->

  <h1 class="title">
    {{ message }}
    <!-- {{ iconImg }} -->

    <!-- ? -->
  </h1>

  <img alt="" v-bind:src="iconImg" class="icon" />
  <!-- <img class="icon" src="../assets/img/icon.png"> -->

  <div id="offers">
    <div class="container text-center">
      <div class="row align-items-end">
        <cards-offers v-for="card in cards" :key="card.id" :offer="card" />
      </div>
    </div>
  </div>
  <br />
  <br />
  <br />

  <ShoppingCart></ShoppingCart>
  <div></div>

  <br />
  <br />
  <Footer></Footer>
</template>

<script>
import ShoppingCart from "../components/ShoppingCart.vue";
import SearchImg from "../components/SearchImg.vue";

import Footer from "../components/Footer.vue";

export default {
  // X
  components: {
    ShoppingCart,
  },

  data() {
    return {
      message: "What is your favorite candle",
      iconImg: "src/assets/img/11.png",
      cards: [],
    };
  },

  // name: 'HomeView',
  components: { "cards-offers": CardsOffers, SearchImg },
  mounted() {
    this.fetchData();
  },

  methods: {
    async fetchData() {
      const response = await fetch("data.json");
      const result = await response.json();
      this.cards = result;
    },
  },
};
</script>

<style scoped>
body {
  background-color: white;
}

#offers {
  display: flex;
  justify-content: center;
  margin-top: 5vh;
  margin-bottom: 10vh;
}

.title,
h1 {
  display: flex;
  justify-content: center;
  margin-top: 10vh;
  color: rgb(131, 62, 15);
}

.icon {
  height: 50px;
  width: 50px;
  margin-left: 1030px;
  margin-top: -110px;
}

@media screen and (min-width: 360px) and (max-width: 980px) {
  body,
  html {
    overflow-x: hidden;
  }

  .title {
    font-size: 20px;
  }
}
</style>
