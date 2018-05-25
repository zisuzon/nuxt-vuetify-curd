<template>
  <v-app>

    <!-- Left Sidebar -->
    <v-navigation-drawer
      :mini-variant.sync="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile
          router
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
    </v-navigation-drawer>
    
     <!-- Top Menu -->
    <v-toolbar fixed app :clipped-left="clipped">
      
      <!-- Toggle Left Sidebar Button -->
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>

      <!-- Toggle to Mini Left Sidebar -->
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon v-html="miniVariant ? 'chevron_right' : 'chevron_left'"></v-icon>
      </v-btn>

      <!-- Full width Top menu -->
      <v-btn
        icon
        @click.stop="clipped = !clipped"
      >
        <v-icon>web</v-icon>
      </v-btn>

      <!-- Title -->
      <v-toolbar-title v-text="title"></v-toolbar-title>
      
      <v-spacer></v-spacer>
    </v-toolbar>

    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

    <!-- Footer -->
    <v-footer class="secondary" app>
      <v-layout row wrap align-center>
        <v-flex xs12>
          <div class="white--text ml-3">
            Made with
            <v-icon class="red--text">favorite</v-icon>
            by <a class="white--text" href="http://www.zisuzon.com/" target="_blank">ZIS</a>
          </div>
        </v-flex>
      </v-layout>
    </v-footer>

  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'home', title: 'Home', to: '/' },
          { icon: 'create', title: 'New Post', to: '/newpost' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vuetify CURD',
        valid: true
      }
    }
  }
</script>
