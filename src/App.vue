<template>
  <v-app>
    <v-app-bar app color="grey darken-3">
      <v-toolbar-title>
        <a style="text-decoration: none; color: white" href="http://localhost:8080/">JSON Editor</a>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <about-button />
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import AboutButton from './components/AboutButton.vue'
export default {
  name: 'App',
  components: {
    AboutButton
  },
  data () {
    return {
    }
  }
};
</script>
