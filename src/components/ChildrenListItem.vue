<template>
  <div class="children-body__item">
    <CustomInput v-model="item.name" :placeholder="'Имя'" />
    <CustomInput v-model="item.age" :placeholder="'Возраст'" />
    <div class="delete-btn" @click="$emit('removeItem', item.id)">Удалить</div>
  </div>
</template>

<script>
import CustomInput from "@/components/UI/CustomInput.vue";

export default {
  name: "ChildrenListItem",
  components: { CustomInput },
  props: {
    item: {
      type: Object,
    },
  },
};
</script>

<style scoped>
.children-body__item {
  display: grid;
  grid-template-columns: 1fr 1fr auto;
  grid-column-gap: 18px;
}

.delete-btn {
  font-size: 14px;
  line-height: 24px;
  color: #01a7fd;
  align-self: center;
  cursor: pointer;
}
</style>
