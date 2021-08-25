<template>
  <v-tooltip bottom open-delay="400">
    <template v-slot:activator="{ on, attrs }">
      <v-btn v-bind="attrs"  v-on="on" text class="white--text" small>
        <v-icon  class="ma-1">mdi-share-variant</v-icon>
        Share
      </v-btn>
    </template>
    <span>Share</span>
  </v-tooltip>
</template>

<script>
export default {
  name: 'ShareButton'
}
</script>

<style>

</style>