<template>
  <v-app>

      <v-content>
        <v-container>
          
          <router-view></router-view>

          <v-dialog
            v-model="dialog"
            hide-overlay
            persistent
            width="300"
          >
            <v-card
              color="primary"
              dark
            >
              <v-card-text>
                Please stand by
                <v-progress-linear
                  indeterminate
                  color="white"
                  class="mb-0"
                ></v-progress-linear>
              </v-card-text>
            </v-card>
          </v-dialog>

        </v-container>
      </v-content>
    
  </v-app>  
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
