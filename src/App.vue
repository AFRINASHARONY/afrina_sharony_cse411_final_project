<template>
  <v-app>
    <Navbar />
    <v-main class="grey lighten-3">
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar.vue";

export default {
  name: "App",
  data() {
    return {};
  },
  components: { Navbar },
};
</script>
