<template>
  <div class="c3js">
    <h1>C3.js</h1>
    <div style="width: 80%; height: 30%; margin: auto;">
      <C3Sample :data="data"></C3Sample>
    </div>
    <button @click="reGenerate">ReGenerate</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import C3Sample from "@/components/C3Sample.vue";

@Component({
  components: {
    C3Sample
  }
})
export default class Home extends Vue {
  private data = {
    columns: [
      ["data1", 30, 20, 50, 40, 60, 50],
      ["data2", 200, 130, 90, 240, 130, 220],
      ["data3", 300, 200, 160, 400, 250, 250],
      ["data4", 200, 130, 90, 240, 130, 220],
      ["data5", 130, 120, 150, 140, 160, 150],
      ["data6", 90, 70, 20, 50, 60, 120]
    ],
    type: "bar",
    types: {
      data3: "spline",
      data4: "line",
      data6: "area"
    },
    groups: [["data1", "data2"]]
  };
  reGenerate(): void {
    const length = Math.floor(Math.random() * 10 + 1);

    const columns = Array(6)
      .fill(0)
      .map((e, i) => {
        return [
          `data${i + 1}`,
          ...Array(length)
            .fill(0)
            .map(_ => {
              return Math.floor((Math.random() + 1) * Math.random() * 10);
            })
        ];
      });

    this.data = {
      ...this.data,
      columns
    };
  }
}
</script>
