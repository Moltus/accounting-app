<template>
  <v-container >
    <v-layout row>
      <v-flex fluid>
        <v-card>
          <v-toolbar dark class="secondary darken-1 mb-3 py-2">
            <v-layout row wrap align-center justify-space-between fill-height class="pt-2">
              <v-flex xs12 sm3>
                <!-- Load component -->
                <SearchField />
              </v-flex>
              <v-flex xs12 sm3>
                <!-- Load component -->
                <DateToDate />
              </v-flex>
              <v-flex xs12 sm3>
                <!-- Load component -->
                <FilterBy />
              </v-flex>
              <v-flex xs12 sm3 >
                <!-- Load component -->
                <ToValidateSwitch />
              </v-flex>
            </v-layout>
          </v-toolbar>
          
          <!-- Load OperationsList component for row creation and expansion panel inside forms -->
            <OperationsList 
              v-bind:opsCategories="opsCategories" v-bind:operations="operations" 
              v-bind:vatRates="vatRates"
            />
            
          
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
  import OperationsList from './main-section-body/OperationsList.vue';

  export default {
    name: "MainSection",
    components: {
      DateToDate,
      ToValidateSwitch,
      SearchField,
      FilterBy,
      OperationsList
    },
    
    data () {
      return {
        
      }
    },
    props: ['operations', 'opsCategories', 'vatRates'],
    
  }
</script>

