<template> 
  <v-select
    :items="items"
    label="Filtrer par..."
    class="px-4"
    color="black"
    prepend-inner-icon="filter_list"
  ></v-select>
</template>

<script>
export default {
  name: "FilterBy",
  data: () => ({
      items: ['Date', 'Montant', 'Catégorie', 'Taux TVA']
    })
}
</script>
