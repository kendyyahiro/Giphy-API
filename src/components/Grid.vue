<template>
  <div>
    <v-card class="mx-auto" max-width="344" min-width="344">
      <v-img
        v-bind:src="src"
        height="200px"
      ></v-img>

      <v-card-title>{{titulo}} </v-card-title>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn>
      </v-card-actions>
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            {{descricao}}
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </div>
</template>
 
<script>
export default {
  data() {
    return;
  },
  name: 'Grid',
  props: {
    titulo: String,
    descricao: String,
    src: String,
    show: false
  },
};
</script>

<style scoped>
.theme--light.v-application {
    background: #000000cc;
    color: rgba(216, 216, 216, 0.87);
}

</style>