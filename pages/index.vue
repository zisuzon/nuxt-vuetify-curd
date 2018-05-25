<template>
  <v-layout row wrap align-center>
    <v-flex xd12>
      <div v-for="post in posts" :key="post.title">
        <v-card class="my-3" hover>
          <v-card-media
            class="white--text"
            height="170px"
            :src="post.imgUrl"
          >
            <v-container fill-height fluid>
              <v-layout>
                <v-flex xs12 align-end d-flex>
                  <span class="headline">{{ post.title }}</span>
                </v-flex>
              </v-layout>
            </v-container>
          </v-card-media>
          <v-card-text>
            {{ post.content }}
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon class="red--text">
              <v-icon medium>delete</v-icon>
            </v-btn>
            <v-btn icon class="light-blue--text">
              <v-icon medium>edit</v-icon>
            </v-btn>
            <v-btn icon class="blue--text text--darken-4">
              <v-icon medium>fa-facebook</v-icon>
            </v-btn>
            <!-- <v-btn flat class="blue--text">Read More</v-btn> -->
          </v-card-actions>
        </v-card>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import postData from '~/data/posts'

export default {
  data () {
    return {
      posts: null
    }
  },
  mounted () {
    this.posts = postData.posts
  }
}
</script>
