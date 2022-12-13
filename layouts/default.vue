<template>
  <v-app>
    <v-main>
      <v-card color="grey lighten-4" flat height="50px" tile>
        <v-toolbar dense>
          <v-app-bar-nav-icon></v-app-bar-nav-icon>

          <v-toolbar-title>Weather App By Putra</v-toolbar-title>

          <v-spacer></v-spacer>

          <v-btn>
            <n-link to="/wheather-app">Weather API</n-link>
          </v-btn>
        </v-toolbar>
      </v-card>
      <transition>
        <nuxt />
      </transition>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: "default",
    };
  },
};
</script>

<style>
a {
  text-decoration: none;
  color: white;
}
</style>
//kenapa style a dikarenakan n-link adalah a href diliat di page source jadi di
ubah text nya yang asalnya biru di jadiin putih memakai text decortaion
