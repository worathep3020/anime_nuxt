<template>
  <div>
    <v-container class="light-blue lighten-5">
      <h1 align="center" class="rainbow">{{ this.$route.params.title }}</h1>
      <v-row class="md-12">
        <v-col class="col-md-4">
          <div align="center">
            <img :src="this.manga.img" />
          </div>
        </v-col>
        <v-col class="col-md-7">
          <br />
          <h4>Rate: {{ this.manga.rate }}</h4>
          <h4>Episodes: {{ this.manga.ep }}</h4>
          <h4>Type: {{ this.manga.type }}</h4>
          <h4>Start: {{ this.manga.start }}</h4>
          <h4>End: {{ this.manga.end }}</h4>
          <v-rating
            v-model="this.manga.star / 2.0"
            length="5"
            color="green"
            background-color="green lighten-3"
            readonly="readonly"
            half-increments="halfIncrements"
          >
          </v-rating>

          <v-card class="black">
            <v-card-text>{{ this.manga.story }}</v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <h1 align="center">
      <v-btn :href="this.manga.url" target="_blank"> Go to Website </v-btn>
    </h1>
  </div>
</template>
<script>
export default {
  data() {
    return {
      manga: this.$route.params,
    }
  },
}
</script>
<style>
h1 {
  color: black;
}
h4 {
  color: black;
}
</style>
