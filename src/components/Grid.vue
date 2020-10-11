<template>
  <div>
    <v-card class="mx-auto" max-width="344" min-width="344">
      <v-img
        v-bind:src="src"
        height="200px"
      ></v-img>
    </v-card>
  </div>
</template>
 
<script>
export default {
  name: 'Grid',
  props: {
    titulo: String,
    descricao: String,
    src: String,
    show: {
      type: Boolean,
      default: false
    }
  },
};
</script>

<style scoped>
.theme--light.v-application {
    background: #000000cc;
    color: rgba(216, 216, 216, 0.87);
}

</style>