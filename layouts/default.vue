<template>
  <v-app id="gim">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      src="https://cdn.vox-cdn.com/thumbor/c4YShhpPqAovZuZqQb3eaGX8I6o=/0x0:1280x720/920x613/filters:focal(613x232:817x436):format(webp)/cdn.vox-cdn.com/uploads/chorus_image/image/66942555/Zekrom_M14.0.png"
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
      src="https://thumbs.gfycat.com/DizzyJollyAnole-small.gif"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <h1>
        <a href="https://myanimelist.net/">
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
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
        {
          icon: 'mdi-account-check',
          title: 'My Profile',
          to: '/Profile',
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
#gim {
  background-image: url(https://i.pinimg.com/originals/77/46/90/774690aeb4e69f4f05d8b828ab892148.jpg);
}
</style>
