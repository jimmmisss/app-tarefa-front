<template>
    <v-navigation-drawer
      :mini-variant.sync="mini"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      
      <v-toolbar flat class="transparent">
        <v-list class="pa-0">
          <v-list-tile id="avatr" avatar>
            <v-list-tile-avatar>
              <img src="https://pbs.twimg.com/profile_images/932277356751933440/I_PDuQkz_400x400.jpg">
            </v-list-tile-avatar>

            <v-list-tile-content>
              <v-list-tile-title>Wesley F Pereira</v-list-tile-title>
            </v-list-tile-content>
            
            <v-list-tile-action>
              <v-btn
                icon
                @click.stop="mini = !mini"
              >
                <v-icon>chevron_left</v-icon>
              </v-btn>
            </v-list-tile-action>
          </v-list-tile>

          <v-list-tile
            :to="item.to"
            :key="i"
            v-for="(item, i) in items"
            exact
          >
          
            <v-list-tile-action>
              <v-icon v-html="item.icon"></v-icon>
            </v-list-tile-action>

            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>

          </v-list-tile>

        </v-list>

      </v-toolbar>
    </v-navigation-drawer>

</template>

<script>
  import Bus from '../Bus'
  export default {
    created () {
      var vm = this
      Bus.$on('fechaDrawer', function(status){
        vm.drawer = status
      })
    },
    destroyed () {
      Bus.off('fechaDrawer')
    },

    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'home', title: 'Visão Geral', to: '/' },
          { icon: 'add_circle', title: 'Adicionar task', to: '/adicionar' },
          { icon: 'view_list', title: 'Listar tasks', to: '/listar' }
        ],
        mini: true,
        miniVariant: false,
        right: null
      }
    }
  }
</script>

<style scope>
#avatr {
  height: 64px;
  background-color:whitesmoke
}
</style>