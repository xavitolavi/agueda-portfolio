<template>
  <div class="footer-container">
    <hr>
    <div class="copy">
      &copy;  2023 - Xavi Florit Pons
    </div>
  </div>
</template>

<script>
  export default {
    name: "WebFooter",

  }
</script>

<style lang="less">
.footer-container {
  background: white;
  width: 100%;
  position: fixed;
  bottom: 0;
  z-index: 30;
  font-size: .8rem;

  hr {
    border: 1px solid rgb(235, 235, 235);
  }
}
</style>