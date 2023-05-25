<template>
  <div class="personal-container">
    <div class="caption">Персональные данные</div>
    <div class="personal-container__inputs">
      <CustomInput v-model="name" :placeholder="'Имя'" />
      <CustomInput v-model="age" :placeholder="'Возраст'" />
    </div>
  </div>
</template>

<script>
import CustomInput from "@/components/UI/CustomInput.vue";

export default {
  name: "Personal",
  components: { CustomInput },
  data() {
    return {
      name: JSON.parse(localStorage.getItem("userInfo"))?.name
        ? JSON.parse(localStorage.getItem("userInfo")).name
        : "",
      age: JSON.parse(localStorage.getItem("userInfo"))?.age
        ? JSON.parse(localStorage.getItem("userInfo")).age
        : "",
    };
  },

  mounted() {
    const userInfo = localStorage.getItem("userInfo");
    if (userInfo) {
      this.name = JSON.parse(userInfo)?.name || "";
      this.age = JSON.parse(userInfo)?.age || "";
    }
  },

  watch: {
    name(nV) {
      if (localStorage.getItem("userInfo")) {
        const uInfo = JSON.parse(localStorage.getItem("userInfo"));
        uInfo.name = nV;
        localStorage.setItem("userInfo", JSON.stringify(uInfo));
      } else {
        localStorage.setItem(
          "userInfo",
          `{"name": "${nV}", "age": "${this.age || ""}"}`
        );
      }
    },

    age(nV) {
      if (localStorage.getItem("userInfo")) {
        const uInfo = JSON.parse(localStorage.getItem("userInfo"));
        uInfo.age = nV;
        localStorage.setItem("userInfo", JSON.stringify(uInfo));
      } else {
        localStorage.setItem(
          "userInfo",
          `{"name": "${this.name || ""}", "age": "${nV}"}`
        );
      }
    },
  },
};
</script>

<style scoped>
.caption {
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  color: #111111;
  margin-bottom: 20px;
}

.personal-container {
  margin-bottom: 35px;
}

.personal-container__inputs {
  display: grid;
  grid-row-gap: 10px;
}
</style>
