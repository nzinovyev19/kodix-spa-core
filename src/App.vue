<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-item exact :to="{ name: 'Services' }" link>
          <v-list-item-action>
            <v-icon>mdi-file-table</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Services</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item :to="{ name: 'Contacts' }" link>
          <v-list-item-action>
            <v-icon>mdi-file-table</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Contacts</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      app
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>kodix-spa-core</v-toolbar-title>
    </v-app-bar>
    <v-main class="main">
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
    };
  },
};
</script>

<style lang="sass">
*
  box-sizing: border-box
.full-height
  height: 100%
.main
  height: calc(100vh - 64px)
  min-height: 600px
  overflow: hidden
</style>
