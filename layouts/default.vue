<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      class="d-md-none"
      fixed
      app
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
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar fixed app>
      <v-app-bar-nav-icon class="d-md-none" @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <nav class="d-none d-md-flex">
        <v-btn plain to="/training">Training</v-btn>
        <!--<v-btn plain><NuxtLink to="/search">Search</NuxtLink></v-btn>-->
        <!-- <v-btn plain to="/blog">Blog</v-btn> -->
        <v-btn plain to="/about">About</v-btn>
        <v-btn plain to="/contact">Contact Us</v-btn>
      </nav>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
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
          title: 'Training',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Blog',
          to: '/inspire',
        },
        {
          icon: 'mdi-apps',
          title: 'About',
          to: '/search',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Contact Us',
          to: '/blog',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
    };
  },
};
</script>
