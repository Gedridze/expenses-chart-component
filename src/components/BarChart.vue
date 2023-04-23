<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  labels: string[]
  data: number[]
}>()

if (props.labels.length !== props.data.length) {
  console.warn('[BarChart.vue] labels and data arrays are of different length')
}
const maxColumnValue = computed(() => Math.max(...props.data))
const columnSizes = computed(() => {
  return props.data.map((el) => (el * 100) / maxColumnValue.value)
})
</script>

<template>
  <div>
    <div class="header"></div>
    <div class="chart-container">
      <template v-for="(dataItem, index) in data" :key="index">
        <div class="column" :style="{ height: `${columnSizes[index]}%` }" :class="{'column--highest': dataItem === maxColumnValue}">
          <div class="data-hint">${{ dataItem }}</div>
        </div>
      </template>
    </div>
    <div class="label-container">
      <div v-for="label in labels" :key="label">{{ label }}</div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import '@/main.scss';
.header {
  height: 20%;
}
.chart-container {
  height: 70%;
  display: flex;
  align-items: end;
  margin-bottom: 1rem;
}
.column {
  position: relative;
  margin: 0 1rem;
  flex: 1;
  &:after {
    content: ' ';
    height: 100%;
    width: 100%;
  background-color: $soft-red;
  display: block;
  border-radius: 1rem;

  }

  &:hover {
    &:after {
      opacity: 80%;

    }
    .data-hint {
      visibility: visible;
    }
  }
}

.column--highest::after {
  background-color: $cyan;
}

.label-container {
  height: 10%;
  display: flex;
  justify-content: space-between;
  div {
    flex: 1;
    text-align: center;
    color: $medium-brown;
  }
}

.data-hint {
  visibility: hidden;
  font-weight: bold;
  border-radius: 1rem;
  width: calc(100% + 0.25rem);
  top: -6rem;
  left: 50%;
  transform: translateX(-50%);
  text-align: center;
  height: 5rem;
  line-height: 2.5;
  position: absolute;
  background-color: $dark-brown;
  font-size: 2rem;
}
@media only screen and (max-width: 600px) {
  .data-hint {
    font-size: 1.6rem;
    line-height: 3;
  }
}
</style>
