<template>
  <v-app>
    <v-container fluid pa-0 ma-0>
      <v-layout row wrap>
        <v-flex shrink>
        
          <SideNav pageTitle="Ma Comptabilité" v-bind:navButtons="navButtons"/>
        </v-flex>
        <v-flex>
          <v-content>
            <TopSection 
              v-bind:topSectionTabs="topSectionTabs" v-bind:mainItems="mainItems"
            />
            <MainSection 
              v-bind:opsCategories="opsCategories" v-bind:operations="operations" 
              v-bind:vatRates="vatRates"
            />
          </v-content>
        </v-flex>
      </v-layout>
    
    
    </v-container>
  </v-app>
</template>

<script>
// import HeaderNav from './components/header/HeaderNav.vue';
import SideNav from './components/side-nav/SideNav.vue';
import TopSection from './components/top-section/TopSection.vue';
import MainSection from './components/main-section/MainSection.vue';


export default {
  name: 'App',
  components: {
    SideNav,
    TopSection,
    MainSection,
  },
  data () {
    return {
      navButtons: [
        {
          id: 1,
          title: 'Dashboard',
          icon: 'mdi-view-dashboard',
          active: false
        },
        {
          id: 2,
          title: 'Mes Comptes',
          icon: 'mdi-checkbook',
          active: false
        },
        {
          id: 3,
          title: 'Annotations auto.',
          icon: 'mdi-pen-plus',
          active: false
        },
        {
          id: 4,
          title: 'Paiements',
          icon: 'mdi-currency-eur',
          active: true
        },
        {
          id: 5,
          title: 'Ajouter Banque',
          icon: 'mdi-bank',
          active: false
        },
        {
          id: 6,
          title: 'Déclarer',
          icon: 'mdi-clipboard-check',
          active: false
        },
        {
          id: 7,
          title: 'Outils de calcul',
          icon: 'mdi-calculator',
          active: false
        },
        {
          id: 8,
          title: "Mode d'Emploi",
          icon: 'mdi-help-circle',
          active: false
        }
      ],
      topSectionTabs: [
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
        }
      ],
      mainItems: [
        {
          id: 1,
          title: 'TRÉSORERIE',
          value: '7649,68€',
          color:'blue',
          icon: 'mdi-treasure-chest'
        },
        {
          id: 2,
          title: 'RECETTES',
          value: '6816,30€',
          color:'success',
          icon: 'mdi-finance'
        },
        {
          id: 3,
          title: 'DÉPENSES',
          value: '-2761,53€',
          color:'secondary',
          icon: 'mdi-receipt'
        },
        {
          id: 4,
          title: 'À VALIDER',
          value: '54',
          color:'primary',
          icon: 'mdi-checkbox-multiple-marked-outline'
        }
      ],
      opsCategories: [
        { id: 1, title: 'Carburants', icon: 'mdi-gas-station', color: 'deep-purple' },
        { id: 2, title: 'Publicités', icon: 'mdi-bullhorn', color: 'green' },
        { id: 3, title: 'Déplacements', icon: 'mdi-train-car', color: 'pink' },
        { id: 4, title: 'Frais Bancaires', icon: 'mdi-bank', color: 'blue' }
      ],
      vatRates: [
        { id: 1, title: 0 },
        { id: 2, title: 5.5 },
        { id: 3, title: 10 },
        { id: 4, title: 20 },
      ],
      operations: [
        {
          id: 1,
          date: '2019-04-26',
          title: "HALL'S BEER",
          amount: '38,32',
          comment: null,
          category: null,
          rate: null,
          file: null
        },
        {
          id: 2,
          date: '2019-04-25',
          title: 'MONOPRIX',
          amount: '134,32',
          comment: null,
          category: null,
          rate: null,
          file: null
        },
        {
          id: 3,
          date: '2019-04-25',
          title: 'TOTAL',
          amount: '74,32',
          comment: 'Lorem ipsum dolor sit amet.',
          category: 1,
          rate: 20,
          file: 'facture012.pdf'
        },
        {
          id: 4,
          date: '2019-04-25',
          title: 'CRÉDIT AGRICOLE',
          amount: '74,32',
          comment: 'Lorem ipsum dolor sit amet.',
          category: 4,
          rate: 10,
          file: 'facture99.pdf'
        },
        {
          id: 5,
          date: '2019-04-25',
          title: 'SNCF',
          amount: '112,60',
          comment: null,
          category: null,
          rate: null,
          file: null
        },
        {
          id: 6,
          date: '2019-04-24',
          title: 'SNCF',
          amount: '34,32',
          comment: 'Lorem ipsum dolor sit amet.',
          category: 3,
          rate: 5.5,
          file: 'facture29.pdf'
        },
        {
          id: 7,
          date: '2019-04-21',
          title: 'SOCIÉTÉ GÉNÉRALE',
          amount: '734,32',
          comment: null,
          category: null,
          rate: null,
          file: null
        },
        {
          id: 8,
          date: '2019-04-22',
          title: 'AXA',
          amount: '234,32',
          comment: 'Lorem ipsum dolor sit amet.',
          category: 2,
          rate: 10,
          file: 'facture59.pdf'
        }
      ]

    }
  }
}
</script>
