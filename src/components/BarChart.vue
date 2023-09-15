<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>

<script>
import { Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: ['TV', 'LapTop', 'Freezer', 'AC', 'Table', 'Chair'],
        datasets: [
          {
            label: 'Products',
            data: [12, 19, 3, 5, 6, 3],
            backgroundColor: 'rgba(103, 140, 249 , 1)'
          }
        ]
      },
      chartOptions: {
        responsive: true
      }
    }
  }
}
</script>
