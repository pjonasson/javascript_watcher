<script>
import { Bar } from "vue-chartjs";

export default {
  extends: Bar,
  props: {
    label: {
      type: String,
    },
    chartData: {
      type: Array,
    },
    options: {
      type: Object,
    },
  },
  mounted() {
    this.renderChart({
      labels: "",
      datasets: [
        {
          label: this.label,
          data: totals,
        },
      ],
    }
    this.options
    );
  }
};
</script>
