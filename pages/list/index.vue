<template>
  <v-container>
      <!-- <pre>{{ test }}</pre> -->

      <v-row app no-gutters>
        <v-btn>New</v-btn>
        <v-btn>Most Active</v-btn>
        <v-btn>No replies</v-btn>
        <v-spacer></v-spacer>
        <v-btn><nuxt-link to="/post/add">Post New Thread</nuxt-link></v-btn>
      </v-row>

      <v-row>

        <v-col
          sm="2"
        >
          <v-card
            class="pa-2"
            outlined
            tile
          >
            Topic
            <ul>
              <li v-for="topic in topics"><a href="">{{ topic.title }}</a></li>
            </ul>
          </v-card>

        </v-col>

        <v-col
          sm="10"
        >
          <!-- <v-card
            class="pa-2"
            outlined
            tile
            v-for="thread in threads"
            :key="thread.id"
          >

            {{ thread.title }}
            
          </v-card> -->

          <v-card
            class="pa-2"
            color="#26c6da"
            dark
            outlined
            tile
            v-for="thread in threads"
            :key="thread.id"
          >
            <v-card-title>
              <v-icon
                large
                left
              >
                mdi-twitter
              </v-icon>
              <span class="title font-weight-light">{{ thread.title }}</span>
            </v-card-title>

            <v-card-text class="headline font-weight-bold">
              {{ thread.description }}
            </v-card-text>

            <v-card-actions>
              <v-list-item class="grow">
                <v-list-item-avatar color="grey darken-3">
                  <v-img
                    class="elevation-6"
                    src="https://avataaars.io/?avatarStyle=Transparent&topType=ShortHairShortCurly&accessoriesType=Prescription02&hairColor=Black&facialHairType=Blank&clotheType=Hoodie&clotheColor=White&eyeType=Default&eyebrowType=DefaultNatural&mouthType=Default&skinColor=Light"
                  ></v-img>
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title>Evan You</v-list-item-title>
                </v-list-item-content>

                <v-row
                  justify="end"
                >
                  <v-icon class="mr-1 ma-5">mdi-heart</v-icon>
                  <span class="subheading mr-2">256</span>
                  <span class="mr-1">·</span>
                  <v-icon class="mr-1">mdi-share-variant</v-icon>
                  <span class="subheading">45</span>
                </v-row>


                <v-row
                  justify="end"
                >
                  <v-btn><nuxt-link to="/post">View Post</nuxt-link></v-btn>
                </v-row>
              </v-list-item>

            </v-card-actions>
          </v-card>

        </v-col>

      </v-row>
  </v-container>
</template>

<script>
  export default {
    async asyncData({ params, $axios }) {
      const topics = await $axios.$get(`/list/`)
      const threads = await $axios.$get(`/card/`)
      return { topics: topics.data, threads: threads.data }
    }
  }
</script>