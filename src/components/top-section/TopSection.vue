<template>
  <div>
    <v-toolbar
      color="info"
      dark
      tabs
    >
      <img src="../../assets/company-logo-white.svg" width="25px">

      <v-toolbar-title>{{pageTitle}}</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>search</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>more_vert</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs
          v-model="tab"
          color="info"
          grow
        >
          <v-tabs-slider color="secondary"></v-tabs-slider>

          <v-tab
            v-for="headerTab in headerTabs"
            :key="headerTab.id"
          >
            {{ headerTab.title }}
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="tab">
      <v-tab-item
        v-for="headerTab in headerTabs"
        :key="headerTab.id"
      >
        <v-card flat>
          <v-container fluid>
            
            <v-layout row wrap>
              <v-flex xs6 sm3 py-2 v-for="mainItem in mainItems" v-bind:key="mainItem.id">
                <h3 class="text-xs-center font-weight-black" v-bind:class="[mainItem.color + '--text text--lighten-2']">{{mainItem.title}}</h3>
                <h2 class="text-xs-center font-weight-black" v-bind:class="[mainItem.color + '--text']">{{mainItem.value}}</h2>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </div>
</template>

<script>
export default {
  name: "HeaderNav",
  data() {
    return {
      tab: null,
      headerTabs: [
        {
          id: 1,
          title: "Compte Chèque USD"
        },
        {
          id: 2,
          title: "Notes de Frais"
        },
        {
          id: 3,
          title: "Mes Espèces"
        },
        {
          id: 4,
          title: "Annotations"
        },
        {
          id: 5,
          title: "Mes Paiements"
        },
      ]
    }
  },
  props: ["pageTitle", "mainItems"]
}
</script>
