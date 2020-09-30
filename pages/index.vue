<template>
  <div>
    <div>
      <v-card>
        <v-toolbar color="black" dark flat>
          <v-text-field
            v-model="textSearch"
            class="mx-4"
            flat
            hide-details
            label="ANIME NAME?"
            prepend-inner-icon="mdi-magnify"
            solo-inverted
          >
          </v-text-field>
          <v-btn depressed large color="error" @click="searchData()"
            >Search</v-btn
          >
        </v-toolbar>
      </v-card>
    </div>
    <v-chip-group column>
      <v-card
        v-for="data in List"
        id="bor"
        :key="data.mal_id"
        class="mx-auto"
        max-width="344"
      >
        <nuxt-link
          :to="{
            name: 'title-ani',
            params: {
              img: data.image_url,
              title: data.title,
              story: data.synopsis,
              star: data.score,
              url: data.url,
              start: data.start_date,
              end: data.end_date,
              rate: data.rated,
              ep: data.episodes,
              type: data.type,
              ran: rainbow,
            },
          }"
        >
          <v-img
            :src="data.image_url"
            height="180"
            class="black--text align-end"
            ><div class="rainbow">{{ data.title }}</div></v-img
          >
        </nuxt-link>
        <v-card-text>สมาชิก:{{ data.members }}</v-card-text>
      </v-card>
    </v-chip-group>
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
<style>
.rainbow {
  font-family: 'Pacifico', cursive;
  text-shadow: 2px 2px 4px #000000;
  font-size: 25px;
  -webkit-animation: rainbow 5s infinite;
  -ms-animation: rainbow 5s infinite;
  animation: rainbow 5s infinite;
}
@keyframes rainbow {
  0% {
    color: orange;
  }
  10% {
    color: purple;
  }
  20% {
    color: red;
  }
  30% {
    color: CadetBlue;
  }
  40% {
    color: yellow;
  }
  50% {
    color: coral;
  }
  60% {
    color: green;
  }
  70% {
    color: cyan;
  }
  80% {
    color: DeepPink;
  }
  90% {
    color: DodgerBlue;
  }
  100% {
    color: orange;
  }
}
</style>
