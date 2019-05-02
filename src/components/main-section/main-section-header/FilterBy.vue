<template> 
  <v-select
    :items="items"
    label="Filtrer par..."
    class="px-4"
  ></v-select>
</template>

<script>
export default {
  name: "FilterBy",
  data: () => ({
      items: ['Montant', 'Catégorie', 'Taux TVA']
    })
}
</script>
