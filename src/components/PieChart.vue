<template>
    <div>
      <GChart id="pie-chart"
       type="PieChart"
       :data="chartData"
       :options="chartOptions"
       />

    </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
    name: 'pie-chart',
    data() {
        return {
            chartData: [
                ['Director', 'Films'],
                ['Hayao Miyazaki', 9],
                ['Isao Takahata', 5],
                ['Yoshifumi Kondō', 1],
                ['Hiroyuki Morita', 1],
                ['Gorō Miyazaki', 2],
                ['Hiromasa Yonebayashi', 2]
            ],

            chartOptions: {
                chart: {
                    "title": "Studio Ghibli films are directed by:",
                    is3D: true,
                },
                backgroundColor: { fill:'transparent' },
                legendTextStyle: { color: '#FFFFFF' }
            }
        }
    },
    props: ['pieChartFilms'],
    components: {
        GChart
    }

}
</script>

<style>

</style>