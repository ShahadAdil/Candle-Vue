<template>
  <!-- Bootstrap cards -->
  <div class="col" style="overflow-wrap: anywhere">
    <div class="card" style="width: 18rem">
      <img :src="offer.image" class="card-img-top" alt="picture" />
      <div class="card-body">
        <h5 class="card-title">{{ offer.name }}</h5>
        <p class="card-text">
          {{ offer.price }}
        </p>
        <a href="#" class="btn btn-primary">Buy</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    offer: {
      required: true,
      type: Object,
    },
  },
};
</script>
<style>
.col {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  width: 300px;
}
a[class="btn btn-primary"] {
  background-color: rgb(168, 102, 57);
  border: none;
}

a[class="btn btn-primary"]:hover {
  background-color: rgb(201, 119, 13);
}

p {
  font-weight: bold;
}

@media screen and (min-width: 360px) and (max-width: 980px) {
  body,
  html {
    overflow-x: hidden;
  }

  .col {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
