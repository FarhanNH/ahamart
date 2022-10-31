<template>
  <v-app>
    <sidebar />
    <v-main>
      <HelloWorld />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Sidebar from "./components/Sidebar.vue";

export default {
  name: "App",

  components: {
    HelloWorld,
    Sidebar,
  },

  data: () => ({
    //
  }),
};
</script>
