<template>
   <BarChart />
  <header>

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/pie">Pie</RouterLink>
        <RouterLink to="/bar">Bar</RouterLink>
      </nav>

  </header>

  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'


// export default {
//   name: 'App',
//   components: { BarChart },
// }

</script>