<template>
  <v-app id="inspire">
    <v-navigation-drawer
      class="red lighten-4"
      v-model="drawer"
      app fixed 
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Subtitle Generator
          </v-list-item-title>
          <v-list-item-subtitle>
            Best video subtitle generator!
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app
    color="red darken-4"
    dark
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Video Subtitle Generator</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

  export default {
    data: () => ({
      drawer: null,
      items: [
          { title: 'Generate', icon: 'mdi-alpha-g-box-outline', to:'/' },
          { title: 'About ', icon: 'mdi-information-outline', to:'/about' },
        ] 
    }),
  }
</script>
