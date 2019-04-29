<template>
  <div>
    <v-toolbar
      color="primary"
      dark
      tabs
    >
      <v-toolbar-side-icon></v-toolbar-side-icon>

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
          color="primary"
          grow
        >
          <v-tabs-slider color="blue"></v-tabs-slider>

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
          <v-card-text>Lorem ipsum dolor sit amet consectetur adipisicing elit. Alias odio necessitatibus quasi nihil totam maxime minus quam soluta velit, dicta, veniam tempore quo corporis iste quisquam atque rem saepe accusamus!</v-card-text>
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
  props: ["pageTitle"]
}
</script>
