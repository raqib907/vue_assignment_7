<template>
  <div class="pie-chart">
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { Pie } from 'vue-chartjs';

const chartCanvas = ref(null);

onMounted(() => {
  // Fetch data or manually create data for the pie chart
  const chartData = {
    labels: ['Red', 'Blue', 'Yellow'],
    datasets: [
      {
        backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56'],
        data: [300, 50, 100],
      },
    ],
  };

  const chartOptions = {
    responsive: true,
    maintainAspectRatio: false,
  };

  // Create the pie chart
  new Pie(chartCanvas.value, {
    data: chartData,
    options: chartOptions,
  });
});

onBeforeUnmount(() => {
  // Clean up any ongoing tasks related to the chart
  // For example, you might need to destroy the chart instance
});
</script>

<style>
/* Add your styles for the pie chart container here */
</style>
