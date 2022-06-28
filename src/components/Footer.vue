<template>
  <footer id="footer" class="mt20">
    <div class="container">
      <a href="https://twitter.com/_k1b3">@_k1b3</a>
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
  font-size: 14px;
  line-height: 3;
  text-align: center;
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  a {
    color: #fff;
    text-decoration: none;
  }
}
</style>