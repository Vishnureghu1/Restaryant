<template>
  <div>
    <h1>Login page</h1>
    <img
      src="https://www.freeiconspng.com/thumbs/login-icon/user-login-icon-29.png"
      alt=""
      class="logo-img"
    />
    <h1>This is sign-up page</h1>

    <div class="register">
      <input type="text" v-model="userObj.email" placeholder="Email" />
      <input
        type="password"
        v-model="userObj.password"
        placeholder="Password"
      />
      <button @click.prevent="login()">Login</button>
      <router-link to="/Signup">Signup</router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Login-page",
  data() {
    return {
      userObj: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async login() {
      try {
        let response = await axios(
          `http://localhost:3000/user?email=${this.userObj.email}&password=${this.userObj.password}`
        );
        if (response.status == 200 && response.data.length > 0) {
          localStorage.setItem("user-info", JSON.stringify(response.data[0]));
          this.$router.push({ name: "Home" });
        }
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push("/home");
    }
  },
};
</script>

<style></style>
