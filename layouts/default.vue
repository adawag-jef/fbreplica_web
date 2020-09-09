<template>
  <div>
    <NavBar/>
    <v-spacer>--</v-spacer>
    <nuxt/>
  </div>
</template>

<script>
import NavBar from '~/components/NavBar'

export default {
  components: {
    NavBar
  }
}
</script>