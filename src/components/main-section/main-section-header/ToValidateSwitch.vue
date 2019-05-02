<template>
  <v-switch color="white" class="pl-4" v-model="switch1" :label="`Afficher opérations à valider`"></v-switch>
</template>

<script>
  export default {
    name: "ToValidateSwitch",
    data () {
      return {
        switch1: true,
      }
    }
  }
</script>

<style scoped>
  .v-input__slot .v-label{
    color: white !important
  }

</style>
