<template>
  <v-app>
    <Navbar id="navbar" />
    <sidebar id="sidebar" />
    <v-btn id="openBtn" @click="showSidebar"></v-btn>
    <v-main>
      <Content id="content" />
    </v-main>
  </v-app>
</template>

<script>
import Content from './components/Content';
import Navbar from './components/Navbar.vue';
import Sidebar from './components/Sidebar.vue';

export default {
  name: 'App',

  components: {
    Content,
    Sidebar,
    Navbar,
  },

  data: () => ({
    //
  }),
  methods: {
    showSidebar() {
      document.getElementById('sidebar').style.left = '0';
    },
  },
};
</script>
<style lang="scss">
@import '@/assets/scss/style';
</style>
