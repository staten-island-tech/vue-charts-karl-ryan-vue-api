<!-- <template>
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
   -->

<template>
    <div class="container">
        <Bar v-if="loaded" :data="chartData" />
    </div>
</template>
  
<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
    name: 'BarGraph',
    components: { Bar },

    props: {
        libraries: Array,
    },

    data() {
        return {
            loaded: false,
            chartData: null
        }
    },
    mounted() {
        this.loaded = false

        try {
            const programs = this.libraries.map(library => library._total_program)

            // const numEachProgram = programs.reduce((num, programs) => {
            //     num[programs] = (num[programs] || 0) + 1;
            //     return num;
            // },
            //     [],
            // );
            
            console.log (programs)

            this.chartData = {
                labels: ['1-199', '200-399', '400-599', '600-799', '800-100000'],
                datasets: [
                    {
                        labels: 'Library Programs',
                        backgroundColor: ['red', 'blue', 'green', 'purple', 'orange'],
                        data: programs,
                    }
                ]
            }

            this.loaded = true
        }
        catch (e) {
            console.error(e);
        }
    }
};
</script>
  
<style scoped></style>