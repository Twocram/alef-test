<template>
  <div class="header">
    <div class="header-container">
      <LogoComponent class="logo" />
      <div class="nav">
        <router-link class="nav-item" to="/form">Форма</router-link>
        <router-link class="nav-item" to="/preview">Превью</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import LogoComponent from "@/components/Icons/LogoComponent.vue";

export default {
  name: "Header",
  components: { LogoComponent },
};
</script>

<style scoped>
.header {
  height: 76px;
  box-shadow: 0 1px 0 rgba(17, 17, 17, 0.1);
  margin-bottom: 30px;
}

.header-container {
  display: flex;
  align-items: center;
  height: 100%;
  max-width: 1266px;
  width: 100%;
  margin: 0 auto;
}

.logo {
  margin-right: 473px;
}

.nav-item {
  font-size: 14px;
  margin-right: 24px;
  line-height: 24px;
  color: rgba(17, 17, 17, 0.48);
}

.nav-item:last-child {
  margin-right: 0;
}
</style>
