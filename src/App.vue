<script setup lang="ts">
import BalanceWidget from './components/BalanceWidget.vue'
import BarChart from './components/BarChart.vue'
import chartData from './data.json'
import type { SpendingData } from './types'

const data = chartData as SpendingData
</script>
<template>
  <div class="content-wrapper">
    <BalanceWidget class="header" />
    <div class="main-container rounded">
      <h2>Spending - Last 7 days</h2>
      <BarChart  class="chart" :labels="data.map((el) => el.day)" :data="data.map((el) => el.amount)" />
      <div class="divider"></div>
        <div class="footer-content">
          <h5>Total this month</h5>
          <div class="content">
            <p>$478.33</p>
            <div class="extra-content">
              <p>+2.4%</p>
              <p>from last month</p>
            </div>
          </div>
        </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '@/main.scss';

h2 {
  color: $dark-brown;
}
h5 {
  color: $medium-brown;
  font-weight: normal;
  font-size: 1.8rem;
}

.content-wrapper {
  flex:1;
  max-width: 80rem;
  height: 80%;
  margin:0 3rem;
  .header {
    margin-bottom: 4rem;
  }
  .main-container {
    height: 50rem;
    padding: 3rem;
    background-color: $very-pale-orange;
    display: flex;
    flex-direction: column;
    .chart {
      flex: 1;
    }
    .divider {
      border: 1px solid $cream;
      margin: 3rem 0
    }
    .footer-content {
      .content {
        display: flex;
        justify-content: space-between;
        & > p {
          color: $dark-brown;
          font-size: 4rem;
          font-weight: bold;
        }
        .extra-content {
          text-align: right;
          p:first-child {
            color: $dark-brown;
            font-weight: bold;
          }
          p:last-child {
            color: $medium-brown;
          }
        }
      }
    }
  }
}

</style>
