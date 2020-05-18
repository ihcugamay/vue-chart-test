<script lang="ts">
import { Component, Mixins } from "vue-property-decorator";
import Chart from "chart.js";
import { Line, mixins } from "vue-chartjs";

@Component({})
export default class LineChartComponent extends Mixins(
  Line,
  mixins.reactiveProp
) {
  // グラフ用のデータ
  private chartData: Chart.ChartData = {
    labels: ["1月", "2月", "3月", "4月", "5月"],
    datasets: [
      {
        type: "line",
        label: "test1",
        data: [20, 10, 30, 40, 30, 20],
        borderColor: "#AA99AA",
        fill: false
      },
      {
        type: "line",
        label: "test2",
        data: [10, 20, 40, 50, 20, 10],
        borderColor: "#AAFFAA",
        fill: false
      },
      {
        type: "bar",
        label: "test3",
        data: [20, 10, 30, 40, 30, 20],
        barPercentage: 0.5,
        backgroundColor: "#AB6666"
      },
      {
        type: "bar",
        label: "test4",
        data: [15, 1, 32, 45, 3, 2],
        barPercentage: 0.5,
        backgroundColor: "#AB66"
      }
    ]
  };

  private chartOptions: Chart.ChartOptions = {
    responsive: true,
    maintainAspectRatio: false,
    scales: {
      xAxes: [
        {
          ticks: {
            display: false
          }
        }
      ],
      yAxes: [
        {
          ticks: {
            display: false
          }
        }
      ]
    },
    layout: {
      padding: {
        left: -10,
        right: 0,
        top: 0,
        bottom: -10
      }
    }
  };

  public mounted() {
    this.renderChart(this.chartData, this.chartOptions);
  }
}
</script>
