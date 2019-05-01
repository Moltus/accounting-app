<template>
  <v-switch v-model="switch1" :label="`Afficher opérations à valider`"></v-switch>
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