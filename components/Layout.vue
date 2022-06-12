<template>
  <div id="app">
  <v-app id="inspire">
    <v-app id="sandbox">
      <v-navigation-drawer
        v-model="primaryDrawer.model"
        :clipped="primaryDrawer.clipped"
        :floating="primaryDrawer.floating"
        :mini-variant="primaryDrawer.mini"
        :permanent="primaryDrawer.type === 'permanent'"
        :temporary="primaryDrawer.type === 'temporary'"
        app
        overflow
        margin-left="5"
        
      >
      <v-list dense>
        <span class="ml-5"><strong>MENU</strong></span>
       <v-list-item link>
            <v-list-item-action>
              <v-icon>mdi-home</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                <Nuxt-link to="/">Home</Nuxt-link>
              </v-list-item-title>
            </v-list-item-content>
        </v-list-item>

         <v-list-item link>
            <v-list-item-action>
              <v-icon>mdi-email</v-icon>
            </v-list-item-action>
  
            <v-list-item-content>
              <v-list-item-title>
                <Nuxt-link to="/post">Post</Nuxt-link>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>

            <v-list-item link>
            <v-list-item-action>
              <v-icon>mdi-email</v-icon>
            </v-list-item-action>
  
            <v-list-item-content>
              <v-list-item-title>
                <Nuxt-link to="/countries">Api Countries</Nuxt-link>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
      </v-list>

            
      <span class="ml-5"><strong>Ajustes</strong></span>
              <v-switch
                class="ml-4"
                v-model="$vuetify.theme.dark"
                primary
                label="Dark"
              ></v-switch>
        
             <v-switch
               class=" ml-4"
               v-model="footer.inset"
               label="Inset"
               primary
             ></v-switch>
      </v-navigation-drawer>
  
      <v-app-bar
        :clipped-left="primaryDrawer.clipped"
        app
      >
        <v-app-bar-nav-icon
          v-if="primaryDrawer.type !== 'permanent'"
          @click.stop="primaryDrawer.model = !primaryDrawer.model"
        ></v-app-bar-nav-icon>
        <v-toolbar-title>HolaMundo!</v-toolbar-title>
      </v-app-bar>
  
      <v-main>
        <v-container fluid>
          <v-row
            align="center"
            justify="center"
          >
            <v-col cols="10">
              <v-card>
                <v-card-text>
                  <v-row>
                    <v-col
                      cols="12"
                      md="12"
                    >
                    </v-col>
                    <v-col
                      cols="12"
                      md="12"
                    >
                      <Nuxt/>
                    </v-col>
                  </v-row>
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
  
      <v-footer
        :inset="footer.inset"
        app
      >
        <span class="px-4">&copy; {{ new Date().getFullYear() }}</span>
      </v-footer>
    </v-app>
  </v-app>
</div>
</template>

<script>
export default {
    el: '#app',
    data() {
        return {
    drawers: ['Default (no property)', 'Permanent', 'Temporary'],
    primaryDrawer: {
      model: null,
      type: 'default (no property)',
      clipped: false,
      floating: false,
      mini: false,
    },
    footer: {
      inset: false,
    },
        }
    },
    mounted() {
    if (localStorage.footer) {
      this.footer = localStorage.footer;
    }
    if (localStorage.$vuetify) {
      this.$vuetify= localStorage.$vuetify;
    }
    
  },
    methods: {
    persist() {
      localStorage.footer = this.footer;
      localStorage.$vuetify = this.$vuetify;
    }
  }
}
</script>
