<template>
  <app-menu :items="items">
    <template #activator="{ attrs, on }">
      <app-btn
        class="text-lowercase mr-2"
        v-bind="attrs"
        v-on="on"
      >
        <span v-text="`v${version}`" />

        <app-chevron-down />
      </app-btn>
    </template>
  </app-menu>
</template>

<script>
  // Utilities
  import { get } from 'vuex-pathify'

  export default {
    name: 'ReleasesMenu',

    computed: {
      items () {
        return [
          { heading: this.$t('documentation') },
          {
            title: '3.x (latest)',
            href: 'https://vuetifyjs.com',
          },
          {
            title: '2.6.x (v2-stable)',
            href: 'https://v2.vuetifyjs.com',
          },
          {
            title: '1.5.x (v1-stable)',
            href: 'https://v15.vuetifyjs.com',
          },
          { divider: true },
          { heading: this.$t('releases') },
          {
            title: this.$t('release-notes'),
            to: {
              name: 'Documentation',
              params: {
                category: 'getting-started',
                page: 'release-notes',
              },
            },
          },
          {
            title: this.$t('github-releases'),
            href: 'https://github.com/vuetifyjs/vuetify/releases',
          },
        ]
      },
      version: get('app/version'),
    },
  }
</script>
