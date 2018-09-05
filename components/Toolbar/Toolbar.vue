<template>
    <v-toolbar 
        fixed
        app 
        :clipped-left="clipped"
        dark color="blue darken-3">

      <v-toolbar-side-icon @click.stop.prevent="ok"></v-toolbar-side-icon>
      
      <v-toolbar-title v-text="title"></v-toolbar-title>

      <v-spacer></v-spacer>

      <!-- <v-toolbar-items>
        <v-btn flat>
          Ajuda
          <v-icon class="espaco" dark>arrow_drop_down</v-icon>
        </v-btn>
      </v-toolbar-items> -->

      <v-btn icon>
        <v-icon>refresh</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>more_vert</v-icon>
      </v-btn>
      
    </v-toolbar>

</template>

<script>
  import Bus from '../Bus'
  export default {
    data () {
      return {
        clipped: false,
        drawer: true,   
        title: 'Supero - Task'
      }
    },
    methods: {
        ok () {
            Bus.$emit('fechaDrawer', this.drawer = !this.drawer)
        }
    }
  }
</script>

<style scope>
.espaco {
  margin-left: 3px
}
</style>