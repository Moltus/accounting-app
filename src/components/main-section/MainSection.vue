<template>
  <v-container >
    <v-layout row>
    <v-flex fluid>
      <v-card>
        <v-toolbar dark class="blue mb-3 py-2">
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
        <v-list>
          <v-list-group
            v-for="operation in operations"
            :key="operation.id"

            no-action
          >
            <template v-slot:activator>
              <v-list-tile>
                <v-list-tile-content >
                  <v-container class="pb-0 pl-0">
                    <v-layout row wrap justify-center align-content-center >
                      <v-flex xs-2 class="cell2" text-xs-center>
                        <p>{{getDayMonthFR(operation.date)}}</p>
                      </v-flex>
                      <v-flex xs-1 class="cell1" text-xs-center>
                        <v-icon class="mr-3" :class="getIcon(operation.category)[1] + '--text'">{{getIcon(operation.category)[0]}}</v-icon>
                      </v-flex>
                      <v-flex xs-2 class="cell2">
                        <v-list-tile-title >{{ operation.title }}</v-list-tile-title>
                      </v-flex>
                      <v-flex xs-3 class="cell3">
                        <p>{{operation.comment}}</p>
                      </v-flex>
                      <v-flex xs-2 class="cell2" text-xs-right>
                        <p>TVA : {{operation.rate ? operation.rate : 0}} %</p>
                      </v-flex>
                      <v-flex xs-2 class="cell2" text-xs-right>
                        <p>{{operation.amount}} €</p>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-list-tile-content>
              </v-list-tile>
            </template>
            <v-list-tile 
              v-if="operation.file == null"  
            >
              <v-list-tile-content>
                <v-list-tile-title class='mt-4'>Test</v-list-tile-title>
         
              </v-list-tile-content>

            </v-list-tile>

            
          </v-list-group>
        </v-list>
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
    },
    props: ['operations', 'opsCategories'],
    methods: {
      getIcon(id) {
        let icon;
        let iconColor;
        for (let i of this.opsCategories) {
          if (i.id == id) {
            icon = i.icon;
            iconColor = i.color;
          }
        }
        icon = icon || 'mdi-alert-circle';
        iconColor = iconColor || 'primary';
        return [icon, iconColor];
      },
      getDayMonthFR(date) {
        let month = new Array("janvier", "fevrier", "mars", "avril", "mai", "juin", "juillet", "aout", "septembre", "octobre", "novembre", "decembre");
        let myDate = new Date(date);
        return myDate.getDay() + ' ' + month[myDate.getMonth()] + ' ' + myDate.getFullYear();
      }
    }
    
  }
</script>

<style scoped>
  .cell1 {
    min-width: 75px;
  }
  .cell2 {
    min-width: 150px;
  }
  .cell3 {
    min-width: 300px;
  }

</style>
