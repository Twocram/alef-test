<template>
  <div class="container">
    <Personal />

    <div class="children-container">
      <div class="children-top">
        <div class="children-top__caption">Дети (макс. 5)</div>
        <div class="add-btn" v-if="children.length < 5" @click="addChildren">
          <PlusComponent class="plus-icon" />
          <span class="add-btn__caption">Добавить ребенка</span>
        </div>
      </div>

      <ChildrenList
        v-if="children.length"
        @removeItem="removeItem($event)"
        :children="children"
      />
    </div>
    <div class="save-btn" @click="saveList">Сохранить</div>
  </div>
</template>

<script>
import PlusComponent from "@/components/Icons/PlusComponent.vue";
import Personal from "@/components/Personal.vue";
import ChildrenList from "@/components/ChildrenList.vue";

export default {
  name: "FormView",
  components: { ChildrenList, Personal, PlusComponent },
  data() {
    return {
      children: [],
    };
  },

  methods: {
    addChildren() {
      const newChildren = {
        id: Date.now(),
        name: "",
        age: "",
      };

      this.children = [...this.children, newChildren];
    },

    removeItem(id) {
      this.children = this.children.filter((item) => item.id !== id);
    },

    saveList() {
      localStorage.setItem("childrenList", JSON.stringify(this.children));
    },
  },

  mounted() {
    const childrenList = localStorage.getItem("childrenList");
    if (childrenList) {
      this.children = JSON.parse(childrenList);
    }
  },
};
</script>

<style scoped>
.children-top__caption {
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  color: #111111;
}

.children-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

.add-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  padding: 10px 20px;
  border: 2px solid #01a7fd;
  border-radius: 100px;
}

.add-btn__caption {
  color: #01a7fd;
  font-size: 14px;
  line-height: 24px;
  position: relative;
}

.plus-icon {
  margin-right: 4px;
}

.save-btn {
  cursor: pointer;
  background: #01a7fd;
  border-radius: 100px;
  padding: 10px 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 118px;
  font-size: 14px;
  line-height: 24px;
  color: #ffffff;
}
</style>
