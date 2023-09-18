<template>
    <Bar :data="chartData" :options="chartOptions" />
  </template>
  
  <script>
  // DataPage.vue
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'Chart4',
    components: { Bar },
    computed: {
        chartData() { return /* mutable chart data */ },
        chartOptions() { return /* mutable chart options */ }
    }
  }
  </script>