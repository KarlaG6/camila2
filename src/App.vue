 
<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense v-for="item in items" :key="item.name">
        <v-list-item link @click="changeView(item.name)" >
          <v-list-item-action >
            <v-icon>{{item.icon}}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{item.name}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>{{ owner.toUpperCase() }}</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container  class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col class="text-center">
            <router-view/>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; 2020-1</span>
      <v-spacer></v-spacer>
      <span>Estructura de datos</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  props: {
    source: String,
  },
  components: {
  },

  data: () => ({
  drawer: null,
  owner: 'Camila Gómez',
  items: [  { icon: 'mdi-home', name: 'Home'},
            { icon: 'mdi-contact-mail', name: 'Contact'},
            { icon: 'mdi-file-tree', name: 'Projects'}
  ]}),
  methods: {
    changeView(menuOption){
      if (menuOption == 'Home'){
        menuOption = ''
      }
      this.$router.push(`/`+menuOption)
    }
  }
};
</script>
