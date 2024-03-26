<template>
  <div class="cardSet" v-if="library">
    <h2>{{ branch }} </h2>
    <h3 v-if="boro">location: {{ boro }}</h3>
  </div>
</template>

<script setup>
const props = defineProps({
  library: Object,
  branch: String,
  boro: String,
})

console.log(props.library)
</script>

<style scoped>
.cardSet {
  background-color: rgba(0, 0, 0, 0.596);
  border: 2px solid brown;
  margin: 3%;
  text-align: center;
  width: 15%;
  color: white
}
</style>