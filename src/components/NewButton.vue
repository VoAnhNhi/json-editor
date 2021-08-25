<template>
  <v-tooltip bottom open-delay="400">
    <template v-slot:activator="{ on, attrs }">
      <v-btn v-bind="attrs"  v-on="on" text class="white--text" small @click="newDoc">
        <v-icon  class="ma-1">mdi-file-outline</v-icon>
        New
      </v-btn>
    </template>
    <span>Open a new, empty document</span>
  </v-tooltip>
</template>

<script>
export default {
  name: 'NewButton',
  methods: {
    newDoc () {
      localStorage.removeItem('json')
      this.$router.go(0)
    }
  }
}
</script>

<style>

</style>