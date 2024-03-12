<!-- <script setup>
import { ref } from 'vue';

const text = ref('')

function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <input :value="text" @input="onInput" placeholder="Type here">
  <p>{{ text }}</p>
</template> -->

<!-- <template>
  <div>

  </div>
</template>

<script setup>
import {ref, OnMounted } from "vue"
import {OnMounted} from 
const library = ref("");
async function getLibrary() {
  let res =await fetch("https://data.cityofnewyork.us/resource/ne9z-skhf.json");
  let data = await res.json();
  library.value = data;
}
OnMounted(()=> {
  getLibrary();
});

</script> -->

<!-- <style scoped>

</style> -->
<!-- <template>
  <div class="container">
    <Bar v-if="loaded" :data="chartData" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data: () => ({
    loaded: false,
    chartData: null
  }),
  async mounted () {
    this.loaded = false

    try {
      const { userlist } = await fetch('/api/userlist')
      this.chartdata = userlist

      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script> -->

<template>
<div class="flexbox">
    <librarySet  
       v-for="library in data"
      :key="library.branch" 
    />   
  </div>

</template>

<script setup>

import {ref, onMounted } from 'vue'
const libraries = ref('')
async function getLibrary() {
  let res = await fetch('https://data.cityofnewyork.us/resource/ne9z-skhf.json' )
  let data = res.json()
  return data;
}
libraries.value = data.branches

onMounted(()=> {
  getLibrary();
  console.log(data);
})
 
/* import CoolData from '@/components/CoolData.vue';
export default {
  data() {
    return {
      libraries: [],
    };
    },
    mounted:function () {
      this.fetchData();
    },
    methods: {
      fetchData: async function () {
        try {
          const result = await fetch(
            `https://data.cityofnewyork.us/resource/ne9z-skhf.json`
          );
          const data = await result.json();
          this.libraries = data.results;
          console.log(data);
          

        } catch (error) {
          console.log(error);
        }
      }
    }
  } */

</script>

<style scoped>

</style>