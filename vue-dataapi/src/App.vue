<template>
   <BarChart />
  <header>

      <nav>
        <RouterLink to="/">Home</RouterLink>
      </nav>

  </header>

  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import BarChart from './components/CoolData.vue'

// export default {
//   name: 'App',
//   components: { BarChart },
// }
</script>