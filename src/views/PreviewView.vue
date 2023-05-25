<template>
  <div class="container">
    <div class="personal-container">
      <div class="caption">Персональные данные</div>
      <div v-if="userInfo" class="personal-info">
        {{ JSON.parse(userInfo)?.name || "" }},
        {{ `${JSON.parse(userInfo)?.age} лет` || "" }}
      </div>
    </div>

    <div class="children-list">
      <div class="caption">Дети</div>
      <template v-if="JSON.parse(childrenList).length">
        <div
          class="children-list__item"
          v-for="item in JSON.parse(childrenList)"
        >
          {{ item.name || "Не указано имя" }},
          {{ item.age ? item.age + " лет" : "Не указан возраст" }}
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: "PreviewView",
  computed: {
    userInfo() {
      return localStorage.getItem("userInfo");
    },

    childrenList() {
      return localStorage.getItem("childrenList");
    },
  },
};
</script>

<style scoped>
.personal-container {
  margin-bottom: 60px;
}

.caption {
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  color: #111111;
  margin-bottom: 20px;
}

.personal-info {
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  color: #111111;
}

.children-list {
  display: flex;
  flex-direction: column;
}

.children-list__item {
  padding: 10px 20px;
  background: #f1f1f1;
  width: fit-content;
  border-radius: 5px;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  color: #000000;
  margin-bottom: 20px;
}

.children-list__item:last-child {
  margin-bottom: 0;
}
</style>
