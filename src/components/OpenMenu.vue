<template>
  <div>
    <v-menu offset-y bottom open-on-hover left>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" text class="white--text" small>
          <v-icon  class="ma-1">mdi-folder-open-outline</v-icon>
            Open
          <v-icon>mdi-menu-down</v-icon>
        </v-btn>
      </template>
      <v-list dense>
        <v-list-item>
          <v-btn text small @click="dialogRecent =! dialogRecent">
            <v-list-item-icon>
              <v-icon>mdi-history</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Open recent file</v-list-item-title>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn text small @click="openFile">
            <v-list-item-icon>
              <v-icon>mdi-laptop</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              Open from disk<input id="input" type="file" @change="loadFile" style="visibility:hidden; display: none"/>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn text small @click="dialogURL =! dialogURL">
            <v-list-item-icon>
              <v-icon>mdi-link</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Open from URL</v-list-item-title>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
      </v-list>
    </v-menu>
    <v-dialog v-model="dialogRecent" max-width="540px">
      <v-card>
        <v-container>
          <v-card-title>Open a recent file</v-card-title>
          <v-card-text>
            <div>
              <label>Search: </label><v-text-field height="30px" placeholder="Enter a document name....." outlined></v-text-field>
            </div>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="white--text"  color="red"  @click="dialogRecent =! dialogRecent">Close</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
    <v-dialog v-model="dialogURL" max-width="540px">
      <v-card>
        <v-container>
          <v-card-title>Open from URL</v-card-title>
          <v-card-text>
            <div>
              <p>Enter a public url.</p>
              <p>Urls which need authentication or do not have CORS enabled cannot be loaded.</p>
            </div>
            <v-text-field outlined></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="white--text"  color="green"  @click="dialogURL =! dialogURL">Open</v-btn>
            <v-btn class="white--text" color="red"  @click="dialogURL =! dialogURL">Close</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
  </div>
</template>

<script t>
export default {
  name: 'OpenMenu',
  data () {
    return {
      items: [
        { title: 'Open recent file', icon: 'mdi-history'},
        { title: 'Open from disk', icon: 'mdi-laptop'},
        { title: 'Open from URL', icon: 'mdi-link'}
      ],
      dialogRecent: false,
      dialogURL: false,
    }
  },
  methods: {
    openFile () {
      document.getElementById('input').click()
    },
    loadFile (ev) {
      const file = ev.target.files[0];
      const render = new FileReader()
      render.onload = ev => {
        this.$emit("load",ev.target.result)
      }
      render.readAsText(file)

    }
  }
}
</script>

<style>

</style>