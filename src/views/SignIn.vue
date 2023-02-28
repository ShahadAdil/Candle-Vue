<template>
  <header>
    <h2 class="signIn">Sign In</h2>
    <div class="register">
      <div>
        <input
          v-model="name"
          type="text"
          placeholder="Enter Name"
          id="name"
          required
        />
      </div>

      <input v-model="email" type="email" placeholder="Enter Email" required />
      <input
        v-model="password"
        type="password"
        placeholder="Enter Password"
        required
      />

      <button id="btn" @click="gotToHome">Sign In</button>
      <h6><a>Forgot your password ?</a></h6>
      <h3 class="name" v-if="name">Welcome {{ name }} !</h3>
    </div>
  </header>
</template>

<script>
import axios from "axios";
export default {
  name: "signIn",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signIn() {
      let result = await axios.post("/signIn", {
        email: this.email,
        password: this.password,
        name: this.name,
      });

      console.log(result);
      // if (result.status == 201) {
      //   localStorage.setItem("user-info", JSON.stringify(result.data));
      // }
    },
    gotToHome() {
      this.$router.push("/");
    },

    computed: {
      name() {
        return this.name;
      },
    },
  },
};
</script>

<style>
.register input,
.signIn,
#btn {
  display: block;
  width: 300px;
  height: 50px;
  margin: 20px auto;
  padding: 20px;
}
.name {
  width: 100%;
  margin-bottom: 100px;
}

.register input,
#btn {
  border: solid rgb(192, 144, 113) 2px;
}

#btn {
  width: 150px;
  border-radius: 5px;
  height: 50px;
  padding: 0;
  background-color: rgb(168, 102, 57);
  font-weight: 600;
}

.signIn,
.name {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 200px;
  font-weight: 700;
  color: rgb(168, 102, 57);
}

h6 {
  display: flex;
  justify-content: center;
  align-items: center;
}

.name {
  margin-top: 70px;
}

.signin-name {
  margin-left: 720px;
}
</style>
