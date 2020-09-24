<template>
    
    <nav>
      <v-toolbar flat app>
          <v-toolbar-title class="text-uppercase grey--text">
              <span class="font-weight-light">Chatter Box</span>
          </v-toolbar-title>
          <v-spacer></v-spacer>

          <div v-if="isAuthenticated">
            <v-btn flat color="grey" class="profile">  
                <nuxt-link to="/list">List</nuxt-link>
            </v-btn>
            <v-btn flat color="grey" class="profile">  
                <nuxt-link to="/post">Comment</nuxt-link>
            </v-btn>
            <v-btn flat color="grey" class="profile">  
                <span>Notification</span>
            </v-btn>
            <v-btn flat color="grey" class="profile">  
              <nuxt-link to="/profile">Admin Settings</nuxt-link>
            </v-btn>
            <v-btn flat color="grey" class="profile">  
              <nuxt-link to="/profile">My Profile</nuxt-link>
            </v-btn>
            <v-btn flat color="grey" class="logout">        
                <a @click="logout">Logout</a>
            </v-btn>
          </div>

          <template v-else>
              <v-btn flat color="grey" class="logout">        
                <nuxt-link to="/">Home</nuxt-link>
              </v-btn>
              <v-btn flat color="grey" class="logout">        
                <nuxt-link to="/list">About</nuxt-link>
              </v-btn>
          </template> 
      </v-toolbar>
    </nav>

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