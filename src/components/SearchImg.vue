<template>
  <div class="form-outline mb-4">
    <input
      class="form-control"
      type="search"
      v-model="searcImg"
      placeholder="Search"
      id="datatable-search-input"
    />
    <label class="form-label" for="datatable-search-input"></label>
    <div class="container">
      <div v-for="item in filteredItems" :key="item.id">
        <img :src="item.image" alt="item.image" />
        <p>{{ item.name }}</p>
        <p>{{ item.price }}</p>
        <p>{{ item.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      searcImg: "",
    };
  },

  computed: {
    filteredItems() {
      return this.items.filter((item) => {
        return item.name.toLowerCase().includes(this.searcImg.toLowerCase());
      });
    },
  },
  mounted() {
    fetch("data.json")
      .then((response) => response.json())
      .then((data) => {
        this.items = data;
      })
      .catch((error) => {
        console.error("Error fetching data: ", error);
      });
  },
};
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 70px;
  margin-top: 200px;
}

input {
  margin-top: 5px;

  align-items: center;
  margin-left: 60px;
  height: 50px;
  width: 90%;
}
.container img {
  width: 100%;
  height: auto;
  right: -100%;
  margin-top: -80px;
}

.container p {
  text-align: center;
  font-size: 1.2rem;
  font-weight: bold;
}

.form-control:focus {
  border-color: black;
  box-shadow: 0 0 5px white;
}

input[class="form-control"] {
  margin-top: 100px;
}

div .container {
  margin-top: 150px;
}
@media screen and (min-width: 360px) and (max-width: 980px) {
  input[class="form-control"] {
    margin-top: 100px;
    width: 270px;
  }

  div .container {
    margin-top: 100px;
  }
}
</style>
