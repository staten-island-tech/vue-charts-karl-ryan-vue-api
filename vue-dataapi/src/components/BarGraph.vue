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
            
        function sortProgram(arr, index) {
            const coolArr = [0, 0, 0, 0, 0]

            arr.forEach(el => {
                if (el < 200) coolArr[0]++
                else if (el < 400) coolArr[1]++
                else if (el < 600) coolArr[2]++
                else if (el < 800) coolArr[3]++
                else coolArr[4]++
        })
            return coolArr[index]
        }

        

        this.chartData = {
            data: ('yes'),
            labels: ['Number Of Programs in Library'],
            datasets: [
                {
                    label: '0-199',
                    backgroundColor: ['red'],
                    data: [sortProgram(programs, 0)],
                },
                {
                    label: '200-399',
                    backgroundColor: ['blue'],
                    data: [sortProgram(programs, 1)],
                },
                {
                    label: '400-599',
                    backgroundColor: ['green'],
                    data: [sortProgram(programs, 2)],
                },
                {
                    label: '600-799',
                    backgroundColor: ['purple'],
                    data: [sortProgram(programs, 3)],
                },
                {
                    label: '800+',
                    backgroundColor: ['orange'],
                    data: [sortProgram(programs, 4)],
                },
            ]
        }

        this.loaded = true
    }
        catch(e) {
        console.error(e);
    }
}
};
</script>
  
<style scoped></style>