<template>
    <Pie id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>
  
<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale } from 'chart.js'



ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale)

export default {
    name: 'PieChart',
    components: { Pie },
    data() {
        return {
            
            chartData: {
                labels: ['1-100', '101-200', '201-300', '301-400', '401-500', '501-600', '601-700', '701-800'],
                datasets: [{ data: [40, 20, 12] }]
            },
            chartOptions: {
                responsive: true
            }
        }
    }
}
</script>

<style scoped>
</style>

<!-- <template>
    <div class="container">
      <Bar v-if="loaded" :data="chartData" />
    </div>
  </template>
  
  <script>
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale)
  
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
        const { userlist } = await fetch('https://data.cityofnewyork.us/resource/ne9z-skhf.json')
        this.chartdata = userlist
  
        this.loaded = true
      } catch (e) {
        console.error(e)
      }
    }
  }
  </script> -->