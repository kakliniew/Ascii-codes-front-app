<script>
import { defineComponent } from 'vue'
import { Bar } from 'vue3-chart-v2'

export default defineComponent({
  name: 'UsageChart',
  extends: Bar,
  props: ['clickedLetters'],
  mounted () {
    this.renderChart({
      labels: this.labelsComputed,
      datasets: [
        {
          label: 'Letter usage',
          backgroundColor: '#f87979',
          data: this.valuesComputed
        }
      ],
    },
    { 
        maintainAspectRatio: false,
        responsive: true,

        scales: {
          yAxes: [{
              ticks: {
                  beginAtZero: true,
                  stepSize: 1,
                  fontColor: "white",
              }
          }],
          xAxes: [{
              ticks: {
                  fontColor: "white"
              }
          }]
        },
        legend: {
                labels: {
                    fontColor: "white",
                }
        },
    })
  },
  computed: {
    labelsComputed(){
      return this.clickedLetters.map(x => x.letter)
    },
    valuesComputed(){
      return this.clickedLetters.map(x => x.clicked)
    }
  }
})
</script>