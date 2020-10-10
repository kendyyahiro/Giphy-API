<template>
    <v-app-bar
      color="deep-purple accent-4"
      dense
      dark
      prominent
    >
    <v-img
        :src="require('../assets/header-logo-8974b8ae658f704a5b48a2d039b8ad93.gif')"
        class="my-3 tamanho-logo"
        contain
        height=""
      />

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="n in 5"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
</template>

<script>
export default {
  props: {
    titulo: String
  }
    
}
</script>

<style scoped>

    #teste{
        width: 75px;
        height: 75px;
    }
    .theme--dark.v-app-bar.v-toolbar.v-sheet{
      background-color: #000 !important;
    }
    .v-toolbar--prominent:not(.v-toolbar--bottom) .v-toolbar__title{
          align-self: auto;
    }
    
</style>