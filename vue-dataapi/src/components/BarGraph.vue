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

            function sortProgram(arr) {
                const coolArr = []
                    let oneArr = 0
                    let twoArr = 0
                    let threeArr = 0
                    let fourArr = 0
                    let fiveArr = 0
                    arr.forEach((el) => {
                    
                    if (el < 200) {
                        oneArr++
                    }
                    if (el >= 200 && el <400) {
                        twoArr++
                    }
                    if (el >= 400 && el <600) {
                        threeArr++
                    }
                    if (el >= 600 && el <800) {
                        fourArr++
                    }
                    if (el >= 800) {
                        fiveArr++
                    }
            })
                    coolArr.push(oneArr)
                    coolArr.push(twoArr)
                    coolArr.push(threeArr)
                    coolArr.push(fourArr)
                    coolArr.push(fiveArr)
                    return coolArr
        }

        this.chartData = {
            data: ('yes'),
            labels: ['1-199', '200-399', '400-599', '600-799', '800-100000'],
            datasets: [
                {
                    label: 'I HATE LIFE',
                    backgroundColor: ['red', 'blue', 'green', 'purple', 'orange'],
                    data: sortProgram(programs),
                }
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