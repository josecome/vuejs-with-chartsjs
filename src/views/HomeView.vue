<script setup>
import { ref, onBeforeMount, onMounted, watch } from 'vue'
import Chart from '../components/Chart.vue'
import Chart2 from '../components/Chart2.vue'
</script>

<template>
  <main>
    <p><strong>Without Props</strong></p>
    <Chart />
    <p><strong>With Props</strong></p>
    <Chart2
      :chartData="{
        labels: ['TV', 'LapTop', 'Freezer', 'AC', 'Table', 'Chair'],
        datasets: [
          {
            label: 'Products',
            data: [12, 19, 3, 5, 6, 3],
            backgroundColor: 'rgba(103, 140, 249 , 1)'
          }
        ]
      }"
      :chartOptions="{
        responsive: true
      }"
    />
  </main>
</template>
