<template>
  <v-app>
    <div row id="navbar">
      <Navbar />
    </div>
    <sidebar />
    <v-main>
      <HelloWorld />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Navbar from "./components/Navbar.vue";
import Sidebar from "./components/Sidebar.vue";

export default {
  name: "App",

  components: {
    HelloWorld,
    Sidebar,
    Navbar,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
#navbar {
  position: absolute;
  width: 100%;
  top: 0;
  left: 250px;
}
.v-main {
  background-color: #f5f8fa;
}
</style>
