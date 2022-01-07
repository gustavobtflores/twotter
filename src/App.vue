<template>
  <Header />
  <UserProfile />
</template>

<script>
import UserProfile from "./components/UserProfile";
import Header from "./components/Header";

export default {
  name: "App",
  components: {
    UserProfile,
    Header,
  },
};
</script>

<style>
@import "./styles/reset.css";

#app {
  font-family: "Roboto", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
