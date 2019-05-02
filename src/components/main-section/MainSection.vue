<template>
  <v-container>
    <v-layout row>
    <v-flex fluid>
      <v-card>
        <v-toolbar dark class="blue ma-0 py-2">
          <v-layout row wrap align-center justify-space-between fill-height class="pt-2">
            <v-flex xs12 sm3>
              <SearchField />
            </v-flex>
            <v-flex xs12 sm3>
              <DateToDate />
            </v-flex>
            <v-flex xs12 sm3>
              <FilterBy />
            </v-flex>
            <v-flex xs12 sm3 >
              <ToValidateSwitch />
            </v-flex>
          </v-layout>
        </v-toolbar>
      </v-card>  
    </v-flex>
  </v-layout>
  </v-container>
</template>

<script>
  import DateToDate from './main-section-header/DateToDate.vue';
  import ToValidateSwitch from './main-section-header/ToValidateSwitch.vue';
  import SearchField from './main-section-header/SearchField.vue';
  import FilterBy from './main-section-header/FilterBy.vue';

  export default {
    name: "MainSection",
    components: {
      DateToDate,
      ToValidateSwitch,
      SearchField,
      FilterBy
    },
    
    data () {
      return {
        
      }
    }
  }
</script>