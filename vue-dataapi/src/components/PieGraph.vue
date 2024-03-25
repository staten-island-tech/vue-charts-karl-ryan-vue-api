<!-- <template>
    <Pie id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>
  
<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale } from 'chart.js'



ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale)

export default {
    name: 'PieGraph',
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
</style> -->

<template>
  <div class="container">
    <Pie class="pie" v-if="loaded" :data="chartData" />
  </div>
</template>

<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale)

export default {
  name: 'PieGraph',
  components: { Pie },

  props: {
    libraries: Array,
    selectedOption: String,
  },

  data() {
    return {
      loaded: false,
      chartData: null
    }
  },

  watch: {
    selectedOption: {
      immediate: true,
      handler() {
        this.updateChartData();
      }
    }
  },

  methods: {
    async updateChartData() {
      this.loaded = false;

    try {

      if (this.selectedOption === 'location') {
      const locations = this.libraries.map(library => library.boro_central_library);
      const countLocations = locations.reduce((num, location) => { num[location] = (num[location] || 0) + 1;
        return num;
      }, 
      []
      );

      this.chartData = {
        labels: Object.keys(countLocations),
        datasets: [
          {
            label: 'Library Locations',
            backgroundColor: ['red', 'blue', 'green', 'purple', 'orange', 'black'],
            data: Object.values(countLocations)
          }
        ]
      };

    } else if (this.selectedOption === 'weeklyHours') {
          const weeklyHoursData = [];

        for (const library of this.libraries) {
          const label = library.boro_central_library;
          const weeklyHours = parseInt(library.weekly_hours_of_public_service);

          if (weeklyHoursData[label]) {
              weeklyHoursData[label] += weeklyHours;
          } else {
            weeklyHoursData[label] = weeklyHours;
          }
      }
      this.chartData = {
        labels: Object.keys(weeklyHoursData),
        datasets: [
          {
            label: 'Weekly Hours of Public Service',
            backgroundColor: ['red', 'blue', 'green', 'purple', 'orange', 'black'],
                data: Object.values(weeklyHoursData)
              }
            ]
          };
    }

      this.loaded = true;
    } catch (e) {
      console.error(e);
      }
    }
  },

  mounted() {
    this.updateChartData();
  }

};
</script>

<style scoped>
</style>