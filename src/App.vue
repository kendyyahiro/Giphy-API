<template>
  <v-app>
    <v-main>
      <Giphy />
    </v-main>
  </v-app>
</template>

<script>
import Giphy from "./components/Giphy";

export default {
  name: "App",

  components: {
    Giphy,
  },

  data: () => ({
    // 
  }),
};
</script>