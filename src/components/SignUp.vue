<template>
  <div>
    <img
      src="https://www.freeiconspng.com/thumbs/login-icon/user-login-icon-29.png"
      alt=""
      class="logo-img"
    />
    <h1>This is sign-up page</h1>

    <div class="register">
      <input type="text" v-model="userObj.name" placeholder="Name" />
      <input type="email" v-model="userObj.email" placeholder="Eamil" />
      <input
        type="password"
        v-model="userObj.password"
        placeholder="Password"
      />
      <button @click.prevent="signUp">Sign up</button>
      <p>
        <router-link to="/login">Login</router-link>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Signup-page",
  data() {
    return {
      userObj: {
        name: "",
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async signUp() {
      try {
        let response = await axios.post("http://localhost:3000/user", {
          name: this.userObj.name,
          email: this.userObj.email,
          password: this.userObj.password,
        });
        if (response.status == 201) {
          alert("sign-up-done");
          localStorage.setItem("user-info", JSON.stringify(response.data));
          this.$router.push("/home");
        } else {
          this.$router.push("/Signup");
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
