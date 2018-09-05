<template>
  <v-app>

    <Drawer />
    <Toolbar />   

    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>    
    
    <v-footer class="pa-3">
    <v-spacer></v-spacer>
    <div>&copy; {{ new Date().getFullYear() }} - Supero Tasks</div>
  </v-footer>
  </v-app>
</template>

<script>
  import Toolbar from '~/components/Toolbar/Toolbar'
  import Drawer from '~/components/Drawer/Drawer'
  export default {
    components: {
      Toolbar,
      Drawer
    },
    data () {
      return {
        fixed: false
      }
    }
  }
</script>