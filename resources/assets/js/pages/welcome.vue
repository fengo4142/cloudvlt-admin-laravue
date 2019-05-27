<template>
  <div>
    <v-toolbar>
      <v-spacer></v-spacer>
      <!-- <v-toolbar-side-icon class="hidden-md-and-up"></v-toolbar-side-icon> -->
      <v-toolbar-items>
        <v-btn flat v-if="authenticated"></v-btn>
        <template v-else>
          <v-btn flat :to="{ name: 'login' }">{{ $t('login') }}</v-btn>
          <v-btn flat :to="{ name: 'register' }">{{ $t('register') }}</v-btn>
        </template>
      </v-toolbar-items>
    </v-toolbar>
    <main>
      <v-content>
        <v-container fluid>
          <v-layout column align-center>
            <div class="display-3 grey--text mt-5">
              {{ title }}
            </div>
            <div class="body-2 my-3">
              Online Gaming Service Based On Cloud System
            </div>
            <img src="/img/v.png" alt="Vuetify.js" class="mt-5">
            <div class="display-2 grey--text mt-5">
              <v-btn round dark class="primary" v-if="authenticated" :to="{ name: 'home'}">Get Started</v-btn>
            </div>
            <div class="body-2 my-3">
              <p v-if="authenticated">{{ $t('you_are_logged_in') }}</p>
              <p v-else>{{ $t('you_are_not_logged_in') }}</p>
            </div>
          </v-layout>
        </v-container>
      </v-content>
    </main>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'welcome-view',
  layout: 'default',

  metaInfo () {
    return { title: this.$t('home') }
  },

  computed: mapGetters({
    authenticated: 'authCheck'
  }),

  data: () => ({
    title: window.config.appName
  })
}
</script>
