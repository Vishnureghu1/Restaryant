<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/add">Add Restaurent</router-link>
    <router-link to="/update">Update Restaurent</router-link>
    <a href="#" @click="logout()">Logout</a>
  </div>
</template>

<script>
export default {
  name: "header",
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style scoped>
.nav {
  background-color: #333;
  overflow: hidden;
  height: 50px;
  display: flex;
  align-items: center;
}
.nav a {
  text-decoration: none;
  color: white;
  padding: 35px;
}
.nav a:hover {
  background-color: red;
}
</style>
