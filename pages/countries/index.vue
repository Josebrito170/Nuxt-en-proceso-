<template>
  <div class="text--white">
      <h2 >API Countries</h2>
      <div class="d-flex mb-6" v-for="(post, index) in Posts" :key="index">
         <v-card
    class="mx-auto"
    max-width="344"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="text-overline mb-4">
          País
        </div>
        <v-list-item-title class="text-h5 mb-1">
          {{post.name.common}}
        </v-list-item-title>
        <v-list-item-subtitle>
            Región: {{post.region}}
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-avatar size="56" >
              <img
                :src="post.flags[1]"  class="img-fluid w-75"
              >
            </v-avatar>
    </v-list-item>

  </v-card>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            Posts: [], 
        }
    },
    mounted(){
        let vue = this;
        axios.get('https://restcountries.com/v3.1/all')
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