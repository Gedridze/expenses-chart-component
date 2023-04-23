<template>
  <div class="container">
    <div class="content">
      <h5>My balance</h5>
      <p>$921.48</p>
    </div>
    <img src="@/assets/logo.svg" alt="logo">
  </div>
</template>
<style lang="scss" scoped>
@import "@/main.scss";
.container {
  display: flex;
  padding: 2rem 3rem;
  border-radius: 2rem;
  background-color: $soft-red;
  justify-content: space-between;
  .content {
    h5 {
      font-weight: normal;
      margin-bottom: 0.4rem;
    }
    p {
      font-weight: bold;
      font-size: 2.6rem;
    }
  }
}


</style>