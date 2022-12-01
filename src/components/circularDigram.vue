<template>
  <div class="main">
    <svg height="160" width="160" viewBox="0 0 160 160">
      <g v-for="(value, index) in sortedValues" :key="index">
        <circle
          :cx="cx"
          :cy="cy"
          :r="radius"
          :stroke="colors[index]"
          :stroke-width="strokeWidth"
          :stroke-dasharray="adjustedCircumference"
          :stroke-dashoffset="calculateStrokeDashOffset(value, circumference)"
          :transform="returnCircleTransformValue(index)"
          fill="transparent"
        />
        <text></text>
      </g>
    </svg>
  </div>
</template>
<script>
export default {
  name: "DonutPieChart",
  data() {
    return {
      angleOffset: -90,
      chartData: [],
      colors: [
        "#6495ED",
        "goldenrod",
        "#cd5c5c",
        "thistle",
        "lightgray",
        "#eee",
        "red",
        "blue",
        "orange",
        "yellow",
      ],
      cx: 80,
      cy: 80,
      radius: 60,
      sortedValues: [],
      strokeWidth: 30,
      values: [230, 308, 520, 130, 200, 42, 12, 123, 321, 85],
    };
  },
  computed: {
    adjustedCircumference() {
      return this.circumference - 2;
    },
    circumference() {
      return 2 * Math.PI * this.radius;
    },
    dataTotal() {
      return this.sortedValues.reduce((acc, val) => acc + val);
    },
  },
  methods: {
    calculateStrokeDashOffset(dataVal, circumference) {
      return circumference - this.dataPercentage(dataVal) * circumference;
    },
    dataPercentage(dataVal) {
      return dataVal / this.dataTotal;
    },
    returnCircleTransformValue(index) {
      return `rotate(${this.chartData[index].degrees}, ${this.cx}, ${this.cy})`;
    },
    calculateChartData() {
      this.sortedValues.forEach((dataVal) => {
        const data = {
          degrees: this.angleOffset,
        };
        this.chartData.push(data);
        this.angleOffset =
          this.dataPercentage(dataVal) * 360 + this.angleOffset;
      });
    },
    sortInitialValues() {
      this.sortedValues = [...this.values].sort((a, b) => b - a);
    },
  },
  mounted() {
    this.sortInitialValues();
    this.calculateChartData();
  },
};
</script>
<style scoped>
.main {
  width: 100%;
  height: 100%;
}
svg {
  /* width: 800px;
  height: 500px; */
}
</style>
