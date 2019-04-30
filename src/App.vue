<template>
  <v-app>
    <HeaderNav pageTitle="Ma Comptabilité" v-bind:mainItems="mainItems" />

    <v-content>
      <SectionHeader v-bind:opsCategories="opsCategories" v-bind:operations="operations" />
    </v-content>
  </v-app>
</template>

<script>
import HeaderNav from './components/header/HeaderNav.vue';
import SectionHeader from './components/section/SectionHeader.vue';

export default {
  name: 'App',
  components: {
    HeaderNav,
    SectionHeader
  },
  data () {
    return {
      mainItems: [
        { id: 1, title: 'TRÉSORERIE', value: '7649,68€', color:'indigo' },
        { id: 2, title: 'RECETTES', value: '6816,30€', color:'teal' },
        { id: 3, title: 'DÉPENSES', value: '-2761,53€', color:'deep-purple' },
        { id: 4, title: 'À VALIDER', value: '54', color:'primary' }
      ],
      opsCategories: [
        { id: 1, title: 'Carburants' },
        { id: 2, title: 'Publicités' },
        { id: 3, title: 'Déplacements' },
        { id: 4, title: 'Frais Bancaires' }
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
          title: 'MONOPRIX',
          amount: '74,32',
          comment: 'Lorem ipsum dolor sit amet.',
          category: 4,
          rate: 20,
          file: 'facture012.pdf'
        },
        {
          id: 4,
          date: '2019-04-26',
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
          date: '2019-04-22',
          title: 'SNCF',
          amount: '34,32',
          comment: 'Lorem ipsum dolor sit amet.',
          category: 3,
          rate: 5.5,
          file: 'facture29.pdf'
        },
        {
          id: 7,
          date: '2019-04-24',
          title: 'FRANPRIX',
          amount: '34,32',
          comment: null,
          category: null,
          rate: null,
          file: null
        },
      ]

    }
  }
}
</script>
