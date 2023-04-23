<script setup lang="ts">
import BalanceWidget from './components/BalanceWidget.vue'
</script>
<template>
  <BalanceWidget />
  <div class="main-container rounded">
    <h2>Spending - Last 7 days</h2>
    <div class="divider"></div>
    <div class="footer">
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
.main-container {
  padding: 3rem;
  background-color: $very-pale-orange;
}
h2 {
  color: $dark-brown;
}
.footer-content {
  h5 {
    color: $medium-brown;
    font-weight: normal;
    font-size: 1.8rem;
  }
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
        color: $medium-brown
      }
    }
  }
}
.divider {
  border: 1px solid $cream;
}
</style>
