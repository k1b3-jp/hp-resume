<template>
  <footer id="footer" class="mt20">
    <div class="container">
      <p>2021 株式会社◯◯</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterItem",
};
</script>

<style scoped lang="scss">
footer {
  position: sticky;
  top: 100vh;
  width: 100%;
  margin-top: 50px;
  background: #0069ae;
  bottom: 0;
  color: #fff;
  font-size: 12px;
  line-height: 140%;
  text-align: center;
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
}
</style>