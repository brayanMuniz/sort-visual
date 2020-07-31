<template>
  <div>{{BarValue}}</div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class Bar extends Vue {
  @Prop({ default: 0 }) readonly BarValue!: number;
}
</script>