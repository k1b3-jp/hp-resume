<template>
  <header>
    <div class="container">
      <h1>ハロプロ履歴書メーカー</h1>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeadItem",
};
</script>

<style scoped lang="scss">
header {
  background-color: #0075c2;
  height: 65px;
  position: relative;
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  h1 {
    color: #fff;
    margin: 0 auto;
    font-size: 24px;
  }
}
</style>