<template>
  <v-container>
    <ChartjsDemo />
  </v-container>
</template>
<script>
const value = [10, 41, 35, 51, 49, 1, 333, 234, 23, 42, 62, 69, 91, 148]

export default {
  inject: ['theme'],
  components: {
    ChartjsDemo: () => import('../components/LineChart')
  },
  data () {
    return {
      series: [{
        name: 'Desktops',
        data: value
      }],
      chartOptions: {
        chart: {
          height: 350,
          type: 'line',
          zoom: {
            enabled: true
          }
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          curve: 'straight'
        },
        title: {
          text: 'Product Trends by Month',
          align: 'left'
        },
        grid: {
          row: {
            colors: ['#f3f3f3', 'transparent'], // takes an array which will be repeated on columns
            opacity: 0.5
          }
        },
        xaxis: {
          range: 60,
          labels: {
            style: {
              colors: ['#00FF00']
            }
          }
        },
        tooltip: {
          theme: [
            (this.$vuetify.theme.dark ? 'dark' : 'light')
          ]
        }
      }
    }
  },
  methods: {
    func () {
      value.push(Math.random() * 100)
      this.$refs.chart.updateSeries([{
        data: value
      }])
    }
  }
}
</script>
