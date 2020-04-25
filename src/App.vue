<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn to="/" class="mr-2">Home</v-btn>
      <v-btn to="/about" class="mr-2">About</v-btn>
      <v-btn to="/contact" class="mr-2">Contact</v-btn>
      <v-btn to="/members" class="mr-2">Members</v-btn>
      <v-btn to="/login" v-if="!getState" @click="changeState()" class="mr-2">Log in</v-btn>
      <v-btn to="/" v-if="getState" @click="changeState()" class="mr-2">Log out</v-btn>
    </v-app-bar>

    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
  },

  data: () => ({
    clientId: process.env.VUE_APP_AUTH0_CONFIG_CLIENTID
  }),
  computed: {
    getState: function () {
      return this.$store.state.userIsAutheticated
    },
  },
  methods: {
    changeState: function () {
      this.$store.state.userIsAutheticated = !this.$store.state.userIsAutheticated
    }
  }
};
</script>
