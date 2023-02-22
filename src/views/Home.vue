<template>
  <div class="home">
    <Header />
    <h1>
      Hello <mark>{{ name }}</mark> Please welecome to our page
    </h1>
  </div>
</template>

<script>
// @ is an alias to /src

import Header from "../components/Header.vue";
export default {
  name: "Home",
  components: {
    Header,
  },
  data() {
    return {
      name: "",
    };
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;
    console.log(
      "this.name = JSON.parse(user).name;",
      (this.name = JSON.parse(user).name)
    );
    if (!user) {
      this.$router.push("/SignUp");
    }
  },
};
</script>
