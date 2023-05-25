<template>
  <div class="input-container">
    <input
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      @focus="isFocused = true"
      @blur="isFocused = false"
      class="input"
    />
    <label :class="{ active: modelValue || isFocused }">{{
      placeholder
    }}</label>
  </div>
</template>

<script>
export default {
  name: "CustomInput",
  props: {
    placeholder: {
      type: String,
      required: false,
    },
    modelValue: {
      type: String,
    },
  },

  data() {
    return {
      isFocused: false,
    };
  },
};
</script>

<style scoped>
.input-container {
  position: relative;
}

.input {
  position: relative;
  border: 1px solid #f1f1f1;
  border-radius: 4px;
  padding: 12px 16px 6px 16px;
  width: 100%;
  min-height: 56px;
  font-size: 14px;
  line-height: 24px;
  color: #111111;
}
.input:focus {
  outline: none;
}

label {
  position: absolute;
  left: 10px;
  top: 20px;
  font-size: 13px;
  line-height: 16px;
  color: rgba(17, 17, 17, 0.48);
  transition: all 0.2s;
  pointer-events: none;
}

label.active {
  top: 6px;
  left: 14px;
  font-size: 12px;
  color: #999;
}
</style>
