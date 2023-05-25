<template>
  <div class="children-body">
    <ChildrenListItem
      @removeItem="$emit('removeItem', $event)"
      v-for="item in children"
      :key="item.id"
      :item="item"
    />
  </div>
</template>

<script>
import CustomInput from "@/components/UI/CustomInput.vue";
import ChildrenListItem from "@/components/ChildrenListItem.vue";

export default {
  name: "ChildrenList",
  components: { ChildrenListItem, CustomInput },
  props: {
    children: {
      type: Array,
    },
  },
};
</script>

<style scoped>
.children-body {
  display: grid;
  grid-row-gap: 10px;
  margin-bottom: 30px;
}
</style>
