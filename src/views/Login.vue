<template>
  <h1>Login</h1>
  <img alt="Vue logo" src="../assets/restro-logo.jpg" width="100">
  <div class="register">
    <input type="email" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="login">Login</button>
    <p><router-link to="/sign-up">Sign Up</router-link></p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Login",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      console.warn("ok", this.name, this.email, this.password);

      let results = await axios.get(
        `http://localhost:3000/users?email=${this.email}&password=${this.password}`
      );

      if (
        (results.status == 201 || results.status == 200) &&
        results.data.length > 0
      ) {
      //  alert("Login successful");
        console.warn(results);

        localStorage.setItem("user-info", JSON.stringify(results.data[0]));
        this.$router.push({ name: "home" });
      } else {
        alert("Failed Login");
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "home" });
    }
  },
};
</script>

<style>
.register input {
  width: 300px;
  height: 50px;
  padding-left: 20px;
  display: block;
  margin-bottom: 25px;
  margin-left: auto;
  margin-right: auto;
  border: 2px solid #db991d;
}

.register button {
  width: 320;
  height: 40px;
  border: 2px solid #db991d;
  background: #db991d;
  padding: 0 10px;
  border-radius: 5px;
}
</style>
