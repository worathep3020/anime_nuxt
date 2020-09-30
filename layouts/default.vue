<template>
  <v-app id="ani">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      src="https://a-static.besthdwallpaper.com/here-comes-sabo-wallpaper-750x1334-812_164.jpg"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
            <v-spacer />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      src="https://wallpapermemory.com/uploads/647/naruto-wallpaper-hd-2048x1080-396624.jpg"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <h1>
        <a href="https://myanimelist.net/" target="_blank">
          <img src="https://myanimelist.net/images/mal-logo-xsmall.png" />
        </a>
      </h1>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'ANIMELIST',
          to: '/',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
    }
  },
}
</script>

<style>
#ani {
  background-image: url(https://cdn.hipwallpaper.com/m/94/41/jCku1d.png);
  background-size: cover;
}
</style>
