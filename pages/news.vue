<template>
  <div>
    <v-flex pb-4 v-for="(article, index) in articles" :key="index" >
      <v-card
        class="mx-auto"
        max-width="600"
      >
        <v-img
          :src="article.urlToImage"
          height="200px"
        ></v-img>

        <v-card-title>
          {{ article.title }}
        </v-card-title>

        <v-card-subtitle>
          {{ dayjs(article.publishedAt).fromNow() }}
        </v-card-subtitle>

        <v-card-text>
          {{ article.description }}
        </v-card-text>

        <v-card-actions>
          <v-btn
            color="blue lighten-2"
            text
            :href="article.url"
            target="_blank"
          >
            Explorar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </div>
</template>

<script>
  import axios from "axios";
  import dayjs from "dayjs";
  import relativeTime from "dayjs/plugin/relativeTime"
  dayjs.extend(relativeTime);
  
  export default {
    data: () => ({
      show: false,
      articles: [],
      dayjs: dayjs,
      url: 'http://newsapi.org/v2/top-headlines?' +
            'country=ve&' +
              'apiKey=key'
    }),

    created() {
      this.getNews();
    },

    methods: {
      async getNews() {
        try {
          const res = await axios.get(`${this.url}`);
          this.articles = res.data.articles;
        } catch (error) {
          console.error(error);
        }
      }
    },
  }
</script>
