<template>
  <header>

      <nav class="ribbon">
        <RouterLink id="navStuff" to="/">Home</RouterLink> 
        <RouterLink id="navStuff" to="/pie">Locations and Hours of Service</RouterLink>
        <RouterLink id="navStuff" to="/bar">Number of Programs</RouterLink>
      </nav>

  </header>

  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<style scoped>
.ribbon{
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin-top: 3vh;
  padding: 3vh;
  background-color: rgba(250, 235, 215, 0.678);
}

#navStuff {
  margin-left: 100px;
  margin-right: 100px;
  font-size: 2rem;
}

</style>