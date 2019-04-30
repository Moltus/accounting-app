<template>
  <v-tabs
    centered
    color="info"
    dark
    icons-and-text
  >
    <v-tabs-slider color="secondary"></v-tabs-slider>

    <v-tab href="#tab-1">
      Paiements
      <v-icon>credit_card</v-icon>
    </v-tab>

    <v-tab href="#tab-2">
      Ajouter banque
      <v-icon>add_circle_outline</v-icon>
    </v-tab>

    <v-tab href="#tab-3">
      Déclarer
      <v-icon>flag</v-icon>
    </v-tab>

    <v-tab-item
      v-for="i in 3"
      :key="i"
      :value="'tab-' + i"
    >
      <v-card flat v-if="i == 1">
        <v-layout row wrap class="pa-3">
          <v-flex xs12 sm4>
            <DateToDate />
          </v-flex>
          <v-flex xs12 sm4>
            <ToValidateSwitch />
          </v-flex>
        </v-layout>
      </v-card>
      <v-card flat v-else>
        <v-card-text pa-3>{{ text }}</v-card-text>
      </v-card>
    </v-tab-item>
  </v-tabs>
</template>

<script>
  import DateToDate from './section-header/DateToDate.vue';
  import ToValidateSwitch from './section-header/ToValidateSwitch.vue';

  export default {
    name: "SectionHeader",
    components: {
      DateToDate,
      ToValidateSwitch
    },
    
    data () {
      return {
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.'
      }
    }
  }
</script>