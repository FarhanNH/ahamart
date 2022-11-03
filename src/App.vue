<template>
  <v-app>
    <Navbar id="navbar" />
    <sidebar id="sidebar" />
    <v-main>
      <Content id="content" />
    </v-main>
  </v-app>
</template>

<script>
import Content from "./components/Content";
import Navbar from "./components/Navbar.vue";
import Sidebar from "./components/Sidebar.vue";

export default {
  name: "App",

  components: {
    Content,
    Sidebar,
    Navbar,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");
html,
body {
  font-family: "Poppins", sans-serif;
}

#app {
  font-family: "Poppins", sans-serif;
}

.v-btn {
  text-transform: unset !important;
}

#navbar {
  position: -webkit-sticky; /* Safari */
  position: sticky;
  width: 90%;
  top: 0;
  left: 195px;
  z-index: 99;
}

#sidebar {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99;
}

#content {
  margin: 50px 100px 0 250px;
}

.v-main {
  background-color: #e1e5e7;
  height: 100vh;
}
</style>
