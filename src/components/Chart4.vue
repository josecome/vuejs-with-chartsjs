<template>
  <Bar
    :data="{
      labels: labels,
      datasets: [
        {
          label: label,
          data: ds,
          backgroundColor: bck
        }
      ]
    }"
    :options="chartOptions"
  />
</template>

<script>
// DataPage.vue
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
import axios from 'axios'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'Chart4',
  components: { Bar },
  data: () => ({
    loaded: false,
    chartData: null,
    labels: null,
    label: null,
    ds: null,
    bck: null,
    tms: 0,
  }),
  methods: {
    async getData() {
      this.loaded = false

      try {
        const d = await axios.get('http://127.0.0.1:3000/data')
        this.chartdata = d.data
        const dd = d.data
        console.log('=====================')
        this.labels = dd.labels
        this.label = dd.datasets[0].label
        this.ds = dd.datasets[0].data
        this.bck = dd.datasets[0].backgroundColor
        this.tms = dd.tms

        this.loaded = true
      } catch (e) {
        console.error(e)
      }
    }
  },
  mounted() {
    this.getData()
  },
  watch: {
    tms(val, prevval) {
        this.labels = this.chartdata.labels
        this.label = this.chartdata.datasets[0].label
        this.ds = this.chartdata.datasets[0].data
        this.bck = this.chartdata.datasets[0].backgroundColor
        this.tms = this.chartdata.tms
    }
  }
}
</script>
