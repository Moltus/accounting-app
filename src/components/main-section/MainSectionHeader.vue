<template>
  <v-card>
    <v-layout row wrap class="pa-3">
      <v-flex xs12 sm4>
        <ToValidateSwitch />
      </v-flex>
      <v-flex xs12 sm4>
        <DateToDate />
      </v-flex>
      <v-flex xs12 sm4>
        <SearchField />
      </v-flex>
    </v-layout>
  </v-card>  
</template>

<script>
  import DateToDate from './main-section-header/DateToDate.vue';
  import ToValidateSwitch from './main-section-header/ToValidateSwitch.vue';
  import SearchField from './main-section-header/SearchField.vue';

  export default {
    name: "SectionHeader",
    components: {
      DateToDate,
      ToValidateSwitch,
      SearchField
    },
    
    data () {
      return {
        
      }
    }
  }
</script>