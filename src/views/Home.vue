<template>
  <v-container>
    <v-card color="green darken-1">
      <v-card-actions>
        <v-btn text> </v-btn>
        <v-spacer></v-spacer>
        <new-button />
        <open-menu @load="value = $event" />
        <save-menu v-bind:value="value" />
        <option-menu />
        <share-button />
      </v-card-actions>
    </v-card>
    <v-card color="orange lighten-2">
      <v-card-actions>
        <v-btn small class="white--text" text >Code</v-btn>
        <v-btn small class="white--text" text >Tree</v-btn>
        <v-btn small class="white--text" text ><v-icon>mdi-format-text-wrapping-overflow</v-icon></v-btn>
        <v-btn small class="white--text" text><v-icon>mdi-sort-variant</v-icon></v-btn>
        <v-btn small class="white--text" text><v-icon>mdi-sort-ascending</v-icon></v-btn>
        <v-btn small class="white--text" text><v-icon>mdi-filter</v-icon></v-btn>
        <v-btn small class="white--text" text><v-icon>mdi-wrench-outline</v-icon></v-btn>
        <v-btn small class="white--text" text><v-icon>mdi-undo</v-icon></v-btn>
        <v-btn small class="white--text" text><v-icon>mdi-redo</v-icon></v-btn>
      </v-card-actions>
    </v-card>
    <v-card>
     <template>
        <v-container fluid>
          <v-textarea color=" black--text" id="text" v-model="value" rows="17"></v-textarea>
        </v-container>
      </template>  
    </v-card>
  </v-container>
</template>

<script type="text/json">
import OpenMenu from '../components/OpenMenu.vue'
import SaveMenu from '../components/SaveMenu.vue'
import OptionMenu from '../components/OptionMenu.vue'
import NewButton from '../components/NewButton.vue'
import ShareButton from '../components/ShareButton.vue'
  export default {
    name: 'Home',
    components: {
      OpenMenu,
      SaveMenu,
      OptionMenu,
      NewButton,
      ShareButton,
    },
       
    data () {
      return {
        value: '{ }',
      }
    },
    methods: {
    }
  }
</script>
