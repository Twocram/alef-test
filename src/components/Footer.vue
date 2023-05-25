<template>
  <div class="footer">
    <div class="footer-container">all rights reserved</div>
  </div>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
.footer {
  height: 76px;
  background: #fafafa;
  box-shadow: 0 1px 0 rgba(17, 17, 17, 0.1);
}

.footer-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  font-size: 13px;
}
</style>
