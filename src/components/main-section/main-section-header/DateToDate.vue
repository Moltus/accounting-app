<template>
  <v-layout row wrap>
    <v-flex xs12 sm6 md4 mr-4>
      <v-menu
        v-model="menu1"
        :close-on-content-click="false"
        :nudge-right="40"
        lazy
        transition="scale-transition"
        offset-y
        full-width
        min-width="290px"
      >
        <template v-slot:activator="{ on }">
          <v-text-field
            v-model="date1"
            label="Date de début"
            prepend-icon="event"
            readonly
            color="white"
            v-on="on"
          ></v-text-field>
        </template>
        <v-date-picker color="success" v-model="date1" @input="menu1 = false"></v-date-picker>
      </v-menu>
    </v-flex>
    <v-flex xs12 sm6 md4>
      <v-menu
        v-model="menu2"
        :close-on-content-click="false"
        :nudge-right="40"
        lazy
        transition="scale-transition"
        offset-y
        full-width
        min-width="290px"
      >
        <template v-slot:activator="{ on }">
          <v-text-field
            v-model="date2"
            label="Date de fin"
            prepend-icon="event"
            readonly
            color="white"
            v-on="on"
          ></v-text-field>
        </template>
        <v-date-picker v-model="date2" @input="menu2 = false"></v-date-picker>
      </v-menu>
    </v-flex>
    <v-spacer></v-spacer>
  </v-layout>
</template>

<script>
  
  export default {
    name: "DateToDate",
    data: () => ({
      // date1 defaults at beginning of the year.
      date1: new Date('2019-01-01').toISOString().substr(0, 10),
      // date2 defaults to today.
      date2: new Date().toISOString().substr(0, 10),
      menu1: false,
      modal: false,
      menu2: false
    })
  }
</script>

