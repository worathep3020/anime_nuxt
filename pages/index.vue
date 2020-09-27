<template>
  <div>
    <input v-model="textSearch" type="text" placeholder="Search Anime!!!" />
    <button @click="searchData()">Go</button>
    <v-card
      v-for="data in List"
      :key="data.mal_id"
      class="mx-auto"
      max-width="344"
    >
      <v-img :src="data.image_url" class="white--text align-end" height="200px">
        <v-card-title>{{ data.title }}</v-card-title>
      </v-img>
      <v-card-actions>
        <v-btn color="green" text>GO</v-btn>
        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="data">
          <v-card-text>{{ data.synopsis }}</v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      List: null,
      textSearch: '',
    }
  },
  methods: {
    searchData() {
      axios
        .get(
          'https://api.jikan.moe/v3/search/anime?q=' +
            this.textSearch +
            '&limit=10'
        )
        .then((response) => {
          this.List = response.data.results
        })
        .catch((err) => {
          // eslint-disable-next-line no-console
          console.log(err)
        })
    },
  },
}
</script>
