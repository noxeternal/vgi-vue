<template>
  <v-app dark>
    <nox-menu />
    <v-content>
      <v-container>
        <nuxt />
    </v-container>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
import NoxMenu from '~/components/NoxMenu.vue'

  export default {
    components: {
      NoxMenu
    },
    data() {
      return {
        clipped: true,
        drawer: true,
        fixed: false,
        miniVariant: false,
        title: 'Video Game Collection'
      }
    }
  }
</script>
