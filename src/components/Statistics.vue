<template>
    <div id="chart">
        <apexchart type="radialBar" height="350" :options="chartOptions" :series="series"></apexchart>
    </div>

</template>

<script>
import ApexCharts from 'apexcharts'
export default {
    name: 'Statistics',
    data:  {

          series: [70],
          chartOptions: {
            chart: {
              height: 350,
              type: 'radialBar',
            },
            plotOptions: {
              radialBar: {
                hollow: {
                  size: '100%',
                }
              },
            },
            labels: ['Cricket'],
          },


        },

      }

}
</script>

<style>

</style>