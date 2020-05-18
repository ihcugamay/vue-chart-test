<template>
  <div id="c3chart"></div>
</template>
<script lang="ts">
import { Component, Vue, Watch, Prop } from "vue-property-decorator";
import C3 from "c3";
import "c3/c3.css";

@Component({})
export default class ComboChart extends Vue {
  public chart: any;
  @Prop({ default: "#c3chart" })
  bindto!: string;
  @Prop({ required: true })
  data!: c3.Data;
  mounted(): void {
    this.chart = C3.generate({
      bindto: this.bindto,
      data: this.data
    });
  }
  @Watch("data", { deep: true })
  onChangeData(val: any): void {
    this.chart.load(val);
  }
}
</script>
