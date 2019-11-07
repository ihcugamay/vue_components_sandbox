<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      temporary
      clipped
      overflow
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
    <v-app-bar
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn
        icon
        large
        href="https://github.com/"
        target="_blank"
      >
        <v-icon size="32px">
          fab fa-github
        </v-icon>
      </v-btn>
      <v-btn
        icon
        large
        @click="toggleBrightness"
      >
        <v-icon size="32px">
          fas fa-adjust
        </v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      class="grey darken-3"
      fixed
      app
    >
      <div class="footer-text">
        &copy; 2019
      </div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      title: 'title'
    }
  },
  methods: {
    toggleBrightness () {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
    }
  }
}
</script>
<style lang="scss" scoped>
.footer-text{
  color: white;
}
</style>
