<template>
  <div>
    <v-tabs
      v-model="tab"
      centered
      fixed-tabs
      color="#fafafa"
      class="pt-3"
      slider-color='secondary darken-1'

    >
      <!-- props from App.vue gets tabs names and Items Values to display -->
      <v-tab
        v-for="topSectionTab in topSectionTabs"
          :key="topSectionTab.id"
          :href="'#tab' + topSectionTab.id"
          class="subheading"
          
      >
        {{ topSectionTab.title }}

      </v-tab>
      <v-tab-item
        v-for="topSectionTab in topSectionTabs"
        :key="topSectionTab.id"
        :value="'tab' + topSectionTab.id"
      >
        <v-container fluid class="pa-3">
          <v-layout row wrap>
            <v-flex xs-3 sm-6 v-for="mainItem in mainItems" v-bind:key="mainItem.id">
              <v-card class="pa-3 ma-3">
                <v-layout row wrap align-end fill-height>
                  <v-flex>
                    <div class="icon-container pa-4" v-bind:class="mainItem.color">
                      <v-icon large class="grey--text text--lighten-4" dark>{{mainItem.icon}}</v-icon>
                    </div>
                  </v-flex>
                  <v-flex>
                    <h3 class="text-xs-right font-weight-light">{{mainItem.title}}</h3>
                    <h2 class=" text-xs-right font-weight-black" v-bind:class="[mainItem.color + '--text']">{{mainItem.value}}</h2>
                  </v-flex>
                </v-layout>
                <v-divider class="my-3"></v-divider>
                <p class="ma-0  grey--text text--darken-1 text-xs-right">3 derniers mois</p>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
export default {
  name: "TopSection",
  data() {
    return {
      tab: null,
    }
  },
  props: ["pageTitle", "topSectionTabs", "mainItems"]
}
</script>

<style>
  .v-tabs__item--active {
    font-weight: 500;
  }
  .icon-container {
    border-radius: 0 0 20px 0;
    box-shadow: 5px 5px 10px #ccc;
    display: inline-block;
  }

  v-icon {
    border-radius: 5px;
  }
</style>
