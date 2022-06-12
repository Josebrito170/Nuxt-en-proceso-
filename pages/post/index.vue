<template>
  <div class="text--white">
      <h2 >POSTS</h2>
      <div class="d-flex mb-6" v-for="post in Posts" :key="post.id">
         <v-card
    class="mx-auto"
    max-width="344"
  >
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    ></v-img>

    <v-card-title>
      {{post.title}}
    </v-card-title>

    <v-card-subtitle>
      {{post.id}}
    </v-card-subtitle>

    <v-card-actions>
      <v-btn
        color="orange lighten-2"
        text
      >
        Explore
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
        icon
        @click="show = !show"
      >
        <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          {{post.body}}
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            show: false,
            Posts: [],
        }
    },
    mounted(){
        let vue = this;
        axios.get('https://jsonplaceholder.typicode.com/posts')
        .then(function(res){
            vue.Posts = res.data;
            console.log(vue.Posts);
        })
    }
}
</script>

<style>
    .d-flex{
        display: flex;
    }
</style>