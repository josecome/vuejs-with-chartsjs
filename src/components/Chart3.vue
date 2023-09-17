<template>
    <div class="container">
      <Bar v-if="loaded" :data="{
        labels: ['TV', 'LapTop', 'Freezer', 'AC', 'Table', 'Chair'],
        datasets: [
          {
            label: 'Products',
            data: [12, 19, 3, 5, 6, 3],
            backgroundColor: 'rgba(103, 140, 249 , 1)'
          }
        ]
      }" />
    </div>
  </template>
  
  <script>
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  import axios from 'axios'

  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'Chart3',
    components: { Bar },
    data: () => ({
      loaded: false,
      chartData: null,
      labels: null,
      label: null,
      ds: null,
      bck: null,
    }),
    async mounted () {
      this.loaded = false
  
      try {
        const d = await axios.get('http://127.0.0.1:3000/data')
        this.chartdata = d.data
        const dd = d.data
        console.log('=====================')
        this.labels = dd.labels
        this.label = dd.datasets[0].label
        this.data = dd.datasets[0].data
        this.bck = dd.datasets[0].backgroundColor
  
        this.loaded = true
      } catch (e) {
        console.error(e)
      }
    }
  }
  </script>