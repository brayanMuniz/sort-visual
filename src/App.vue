<template>
  <div id="app">
    <Bar v-for="(num, idx) in currentOrder" :key="idx" :BarValue="num" />
  </div>
</template>

<script lang="ts">
import { Vue, Component, Emit, Prop } from "vue-property-decorator";
import Bar from "@/components/Bar.vue";
import "vue-class-component/hooks";

@Component({
  components: {
    Bar,
  },
})
export default class App extends Vue {
  pastOrder: Array<Array<number>> = []; // this will be the history of all the mutations in the array
  currentOrder: Array<number> = [];

  mounted() {
    this.currentOrder = this.generateRandomNumbers();
    this.pastOrder.push(this.currentOrder);
    console.log(this.pastOrder);
  }

  // Methods
  @Emit()
  generateRandomNumbers(amountBars?: number, max?: number): Array<number> {
    if (amountBars == undefined) amountBars = 10;
    if (max == undefined) max = 10;

    const result: Array<number> = [];
    for (let i = 0; i < amountBars; i++) {
      result.push(Math.floor(Math.random() * max));
    }
    return result;
  }
}

// Dont even need to make a bar yet, just be able to line up the numbers and move them around in animate them in a way that shows the steps of each algorithim

// Be able to move the bars and pass in values before giving the sort order
// make them green and such
</script>

