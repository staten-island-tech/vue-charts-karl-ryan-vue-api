<template>
    <Bar :data="chartData" />
</template>
  
<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
    name: 'BarChart',
    components: { Bar },
    data() {
        return {
            chartData: {
                labels: ['1-200', '201-400', '401-600', '601-800', '801+'],
                datasets: [
                    {
                        label: 'Total Programs',
                        backgroundColor: '#f87979',
                        data: [200]
                    }
                    
                ]
            }
        }
    }
}
</script>
  