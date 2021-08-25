<template>
  <div>
    <v-menu offset-y bottom open-on-hover left>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" text class="white--text" small>
          <v-icon  class="ma-1">mdi-cog-outline</v-icon>
            Options
          <v-icon>mdi-menu-down</v-icon>
        </v-btn>
      </template>
      <v-list dense>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
        >
          <v-btn text small>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
export default {
  name: 'OptionMenu',
  data () {
    return {
      items: [
        { title: 'JSON Schema', icon: 'mdi-file-check'},
        { title: 'Indentation', icon: 'mdi-information-variant'},
        { title: 'Document properties', icon: 'mdi-format-indent-increase'},
        { title: 'Delete document', icon: 'mdi-close'}
      ]
    }
  }
}
</script>

<style>

</style>