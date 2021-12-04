<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
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
    <v-app-bar
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-switch
        v-model="$vuetify.theme.dark"
        inset
        label="Modo oscuro"
      ></v-switch>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      app
    >
      <span>&copy; {{ new Date().getFullYear() }} LuxApp | Noticias</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: true,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Bienvenido',
          to: '/'
        },
        {
          icon: 'mdi-newspaper',
          title: 'Noticias',
          to: '/news'
        },
        {
          icon: 'mdi-account-group',
          title: 'Acerca de nosotros',
          to: '/about'
        }
      ],
      dark: 'mdi-theme-light-dark',
      title: 'LuxApp | Noticias'
    }
  },

  props: {
      attrs: {
        type: Object,
        default: () => ({}),
      },
    },
}
</script>
