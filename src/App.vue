<template>
  <Header />
  <Contact />
  <Footer />
</template>

<script>
import Header from "./components/Header";
import Contact from "./components/Contact";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Contact,
    Footer,
  },
};
</script>

<style>
html {
  height: 100%;
}
body {
  background: #f6f6f6;
  margin: 0;
  padding: 0;
  height: 100%;
}
#app {
  font-family: "Hiragino Sans", "ヒラギノ角ゴシック", "メイリオ", Meiryo,
    "ＭＳ Ｐゴシック", "MS PGothic" "ＭＳ ゴシック", "Helvetica Neue",
    "Helvetica", "Arial", sans-serif;
  text-align: center;
  color: #3a5584;
  margin: 0;
  padding: 0;
  height: 100%;
}
</style>
