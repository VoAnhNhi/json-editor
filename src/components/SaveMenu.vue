<template>
  <div>
    <v-menu offset-y bottom open-on-hover left>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" text class="white--text" small>
          <v-icon  class="ma-1">mdi-content-save-outline</v-icon>
            Save
          <v-icon>mdi-menu-down</v-icon>
        </v-btn>
      </template>
      <v-list dense>
        <v-list-item>
          <v-btn text small @click="dialogCloud =! dialogCloud">
            <v-list-item-icon>
              <v-icon>mdi-cloud</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Save to cloud</v-list-item-title>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn text small @click="dialogDisk =! dialogDisk">
            <v-list-item-icon>
              <v-icon>mdi-laptop</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Save to disk</v-list-item-title>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn text small @click="dialogURL =! dialogURL">
            <v-list-item-icon>
              <v-icon>mdi-link</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Save to URL</v-list-item-title>
            </v-list-item-content>
          </v-btn>
        </v-list-item>
      </v-list>
    </v-menu>
    <v-dialog v-model="dialogCloud" max-width="540px">
      <v-card>
        <v-container>
          <v-card-title>Save to cloud</v-card-title>
          <v-card-text>
            <p>Enter a name for the document: </p>
            <v-text-field outlined></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="white--text" color="green lighten-1">Save</v-btn>
            <v-btn class="white--text" color="red darken-2" @click="dialogCloud =! dialogCloud">Cancel</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
    <v-dialog v-model="dialogDisk" max-width="540px">
      <v-card>
        <v-container>
          <v-card-title>Save to disk</v-card-title>
          <v-card-text>
            <p>Enter a name for the document: </p>
            <v-text-field outlined v-model="nameFile"></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="white--text" color="green lighten-1" @click="saveFile">Save</v-btn>
            <v-btn class="white--text" color="red darken-2" @click="dialogDisk =! dialogDisk">Cancel</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
    <v-dialog v-model="dialogURL" max-width="540px">
      <v-card>
        <v-container>
          <v-card-title>Send to URL</v-card-title>
          <v-card-text>
            <p>Enter a public url of a server.</p>
            <p>When clicking Save, an HTTP POST request will be send to the selected url with the JSON document as body. The url must not require authentication and must have CORS enabled.</p>
            <v-text-field outlined ></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="white--text" color="green lighten-1">Save</v-btn>
            <v-btn class="white--text" color="red darken-2" @click="dialogURL =! dialogURL">Cancel</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: 'SaveMenu',
  props:{
    value: String
  },
  data () {
    return {
     dialogCloud: false,
     dialogDisk: false,
     dialogURL: false,
     nameFile: ''
    }
  },
  methods: {
    saveFile () {
      const dataObject = JSON.parse(this.value)
      const data = JSON.stringify(dataObject)
      const blob = new Blob([data], {type: 'text/plain'})
      const e = document.createEvent('MouseEvents'),
      a = document.createElement('a');
      a.download = this.nameFile+".json";
      a.href = window.URL.createObjectURL(blob);
      a.dataset.downloadurl = ['text/json', a.download, a.href].join(':');
      e.initEvent('click', true, false, window, 0, 0, 0, 0, 0, false, false, false, false, 0, null);
      a.dispatchEvent(e);

      this.nameFile = ''
      this.dialogDisk = false

    }
  }
}
</script>

<style>

</style>