<template>
    
  <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      elevate-on-scroll
      scroll-target="#scrolling-techniques-7"
      class="navbar"
    >
      <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->
        <nuxt-link class="default-color" to="/">
            <v-toolbar-title class="navbar-heading"><v-icon class="navbar-icon">mdi-chat</v-icon>Chatter Box</v-toolbar-title>
        </nuxt-link>

      <v-spacer></v-spacer>

    <div v-if="isAuthenticated">
        <v-btn icon>
            <v-icon>mdi-login</v-icon>
        </v-btn>
        <a class="navbar-link">
            {{ loggedInUser.username }}
        </a>
        <div class="">
            <nuxt-link class="navbar-item" to="/profile">My Profile</nuxt-link>
            <hr class="navbar-divider">
            <a class="navbar-item" @click="logout">Logout</a>
        </div>

        <v-select
          :items="items"
          label="Solo field"
          solo
        ></v-select>
    </div>
    
    <template v-else>
     <nuxt-link to="/register" class="navbar-icon"><v-btn rounded color="primary" dark>Register</v-btn></nuxt-link>
     <nuxt-link to="/login"><v-btn rounded color="primary" dark>Log In</v-btn></nuxt-link>
    </template>

    </v-app-bar>
  </v-card>
</template>


<style scoped>

@import url("https://fonts.googleapis.com/css?family=Questrial");

.navbar {
    background-color: tomato!important;
}

.navbar-heading {
    font-family: 'Questrial'!important ;
    font-weight: bolder!important;
}

.navbar-icon {
    margin-right: 5px;
}

.default-color {
    color: #752d21!important;
}


</style>

<script>
import { mapGetters } from 'vuex'

export default {
  computed: {
    ...mapGetters(['isAuthenticated', 'loggedInUser'])
  },
  methods: {
    async logout() {
      await this.$auth.logout();
    },
  },
}
</script>