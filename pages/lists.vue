<template>

<v-flex d-flex>
   <v-layout wrap>
       <v-flex md4 v-for="todo in todos" :key="todo.id">
    
  <v-card
    class="mx-auto"
    color="#26c6da"
    dark
    max-width="400"
  >

    <v-card-title>
      <v-icon
        large
        left
      >
        mdi-twitter
      </v-icon>
      <span class="title font-weight-light">{{ todo.title }}</span>
    </v-card-title>

    <v-card-text class="headline font-weight-bold">
      "Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well."
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
          <v-list-item-title>{{ todo.created_by.name }}</v-list-item-title>
        </v-list-item-content>

        <v-row
          align="center"
          justify="end"
        >
          <v-icon class="mr-1">mdi-heart</v-icon>
          <span class="subheading mr-2">256</span>
          <span class="mr-1">·</span>
          <v-icon class="mr-1">mdi-share-variant</v-icon>
          <span class="subheading">45</span>
        </v-row>
      </v-list-item>
    </v-card-actions>
  </v-card>

        </v-flex>
   </v-layout>
</v-flex>
  
</template>

<script>
export default {
  data() {
    return {
      todos: []
    }
  },
  async fetch() {
    const { data } = await this.$axios.get(
      `http://localhost:8000/api/list/`
    )
    // `todos` has to be declared in data()
    this.todos = data
  },
  
}
</script>