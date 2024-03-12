<script setup>

const props = defineProps( {
    Library: Object,

})
    
</script>

<template>
<div class="cardSet">
    <h2>{{ Library.branches }}</h2>
  </div>
</template>

<style lang="scss" scoped>

</style>