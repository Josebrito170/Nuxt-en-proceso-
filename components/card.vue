<template>
  <v-card
    class="mx-auto"
    max-width="344"
  >
    <!--<v-img
      :src="post.flags[0]" :alt="`bandera-${post.name}`"
      height="200px"
    ></v-img>-->

    <v-card-title>
      {{post.name.common}}
    </v-card-title>

    <v-card-subtitle>
      Población: {{numeroFormato(pais.population)}}
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
          Capital: {{post.capital}}
        </v-card-text>
        <v-card-text>
           Región: {{post.region}}        
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      show: false,
    }),
  }
</script>