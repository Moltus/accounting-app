
<template>
  <v-list>
    <v-list-group
      v-for="operation in operations"
      :key="operation.id"

      no-action
    >
      <template v-slot:activator>
        <v-list-tile @click="activeRow = 'row' + operation.id" :class="{ 'secondary lighten-3' : activeRow === 'row' + operation.id }">
          <v-list-tile-content>
            
            <v-container class="pb-1 pl-0">
              <v-layout row wrap justify-center align-content-center >
                <v-flex xs-2 class="cell2" text-xs-center>
                  <p>{{getDayMonthFR(operation.date)}}</p>
                </v-flex>
                <v-flex xs-1 class="cell1" text-xs-center>
                  <v-icon class="" :class="getIcon(operation.category)[1] + '--text'">{{getIcon(operation.category)[0]}}</v-icon>
                </v-flex>
                <v-flex xs-2 class="cell2">
                  <v-list-tile-title >{{ operation.title }}</v-list-tile-title>
                </v-flex>
                <v-flex xs-3 class="cell3">
                  <p v-bind:class="[operation.comment ? '' : 'primary--text']">{{operation.comment ? operation.comment : 'En attente de validation.'}}</p>
                </v-flex>
                <v-flex xs-2 class="cell2" text-xs-right>
                  <p>{{operation.rate ? 'TVA : ' + operation.rate + ' %': ''}}</p>
                </v-flex>
                <v-flex xs-2 class="cell2" text-xs-right>
                  <p>{{operation.amount}} €</p>
                </v-flex>
              </v-layout>
            </v-container>
          </v-list-tile-content>

          
        </v-list-tile>
      </template>
      
      <form 
      action=""
      v-if="operation.file === null"  
      class=" grey lighten-3"
      >
        <v-container>
          <v-layout align-start justify-center row fill-height>
            <v-flex>
              <label for="category">Catégorie :</label>
              <v-radio-group column v-model="categoryRadio">
                <v-radio 
                  v-for="category in opsCategories" 
                  :key="category.id"
                  v-bind:label="category.title"
                  v-bind:color="category.color"
                  v-bind:value="category.title"
                ></v-radio>
              </v-radio-group>
            </v-flex>
            <v-flex>
              <label for="comment">Commentaire :</label><br><br>
              <textarea class="white" name="comment" id="comment" cols="60" rows="6"></textarea>
            </v-flex>
            <v-flex>
              <label for="">Taux de TVA : </label>
              <v-radio-group column v-model="vatRateRadio">
                <v-radio 
                  v-for="vatRate in vatRates" 
                  :key="vatRate.id"
                  v-bind:label="vatRate.title"
                  v-bind:value="vatRate.title"
                  color="grey darken-3"
                ></v-radio>
              </v-radio-group>
            </v-flex>
            <v-flex>
              <label for="income">Télécharger facture :</label>
              <br><br>
              <!-- <input type="file" name="income" id="income"> -->
              <v-btn
                :loading="loading"
                :disabled="loading"
                color="blue-grey"
                class="white--text"
                @click="loader = 'loading'"
              >
                Fichier
                <v-icon right dark>cloud_upload</v-icon>
              </v-btn>
              <br><br>
              <!-- <input type="submit" value="Valider l'opération"> -->
              <v-btn color="primary" type="submit" value="validate">Valider l'opération
                <v-icon right dark>check_circle</v-icon>
              </v-btn>
            </v-flex>
          </v-layout>
        </v-container>
      </form>
    </v-list-group>
  </v-list>
</template>

<script>
export default {
  name: "OperationsList",
  props: ['operations', 'opsCategories', 'vatRates'],
  data() {
    return {
      activeRow: 'row2',
        categoryRadio: 'Publicités',
        vatRateRadio: '0',
        loader: null,
        loading: false,
    }
  },
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
    },
    watch: {
      loader () {
        const l = this.loader
        this[l] = !this[l]

        setTimeout(() => (this[l] = false), 2000)

        this.loader = null
      }
    }
  }
</script>

<style scoped>
  v-list-tile.active {
    background-color: '#fe7e3c';
  }
  .cell1 {
    min-width: 75px;
  }
  .cell2 {
    min-width: 150px;
  }
  .cell3 {
    min-width: 300px;
  }

  .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }

</style>
