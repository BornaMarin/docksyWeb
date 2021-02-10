<template>
  <v-app dark>
    <v-navigation-drawer
      :mini-variant="miniVariant"
      clipped
      fixed
      app
    >
<!--      :color="$vuetify.theme.dark ? $vuetify.theme.themes.light.primary : $vuetify.theme.themes.dark.primary"-->
<!--      :color="$vuetify.theme.dark ? $vuetify.theme.themes.light.primary : $vuetify.theme.themes.dark.primary"-->
<!--      :color="$vuetify.theme.dark ? $vuetify.theme.themes.light.primary : $vuetify.theme.themes.dark.primary"-->
<!--      :color="$vuetify.theme.dark ? $vuetify.theme.themes.light.primary : $vuetify.theme.themes.dark.primary"-->
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
            <v-list-item-title v-text="item.title"  />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      clipped-left
      fixed
      app
    >
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-switch
        v-model="$vuetify.theme.dark"
        label="Theme"
        hide-details
      ></v-switch>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      fixed
      app
    >
      <span>{{ footer }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
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
          title: 'Docs',
          to: '/docs'
        },
        {
          icon: 'mdi-account',
          title: 'Author',
          to: '/author'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Docksy',
      footer: 'Docksy -v0.1'
    }
  },
  async created() {
    let url = 'https://student-sport-results.herokuapp.com/api/metas/get'
    const res = await this.$axios.get(url)
    console.log(res.data)
    this.footer = res.data.footer
    this.$vuetify.theme.dark = res.data.theme
    this.$vuetify.theme.themes.light.primary = res.data.primaryLight
    this.$vuetify.theme.themes.dark.primary = res.data.primaryDark
  }
}
</script>
