<template>
<div class="cardSet">
    <h2>{{ pokemon.name }}</h2>
  </div>
</template>

<script setup>

const props = defineProps( {
    pokemon: Object,

})
    
</script>

<style lang="scss" scoped>

</style>