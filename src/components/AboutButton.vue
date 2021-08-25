<template>
  <div>
    <v-btn class="ma-4 white--text" text rounded @click="dialogAbout =! dialogAbout">About</v-btn>
    <v-dialog v-model="dialogAbout" max-width="960px">
      <v-card>
        <v-container>
          <v-card-title>About</v-card-title>
          <v-card-text>
            <p>Version: 5.10.0 (changelog), copyright © 2021 .
              JSON Editor  is a web-based tool to view, edit, and format JSON. 
              It shows your data side by side in a clear, editable treeview or a code editor. 
              You can store documents locally or in the cloud.
            </p>
            <v-row >
              <v-col cols="12" sm="4">
                <div>
                  <b>Report a bug</b>
                  <p>If you encounter a bug or have questions or suggestions for improvements, please report this at https://github.com/xxx/xxx/issues/.</p>
                </div>
                  <b>Source code</b>
                  <p>The source code of the main component of this web application, JSONEditor, is open source. You can find it at https://github.com/xxx/xxx.</p>
              </v-col>
              <v-col cols="12" sm="4">
                <div>
                  <b>Data policy</b>
                  <p> No data is shared anywhere except when you save a document in the cloud. Cloud documents are publicly accessible for anyone who has the document id.
                  <br/>DO NOT SAVE SENSITIVE DATA USING THE CLOUD FUNCTIONALITY
                  </p>
                </div>
                <div>
                  <b>Privacy policy</b>
                  <p> This site uses cookies and similar tracking technologies such as the Common ID cookie to provide its services. Click here for information or to opt out.</p>
                </div>
              </v-col>
            </v-row>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn @click="dialogAbout =! dialogAbout" text color="blue">Close</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    name: 'AboutButton',
    data () {
      return {
        dialogAbout: false,
      }
    }
}
</script>

<style>

</style>