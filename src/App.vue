<template>
  <side-bar />
  <index-page />
</template>

<script>
import IndexPage from "./components/IndexPage.vue";
import SideBar from "./components/SideBar.vue";

export default {
  name: "App",
  components: {
    SideBar,
    IndexPage,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins&family=Raleway:wght@300;400&display=swap");

html {
  font-family: "Poppins", sans-serif;
  font-size: 14px;
  box-sizing: border-box;
}

body {
  margin: 0;
}

#app {
  display: flex;
  margin: 0;
  padding: 0;
  min-height: 100vh;
}

ul {
  padding: 0;
  margin: 0;
  width: 100%;
}

li {
  list-style: none;
}

a,
a:visited {
  text-decoration: none;
  color: inherit;
}
</style>
