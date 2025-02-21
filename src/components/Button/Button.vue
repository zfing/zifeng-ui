<template>
  <button
    :class="['my-button', `my-button--${type}`, { 'my-button--disabled': disabled }]"
    :disabled="disabled"
    @click="handleClick"
  >
    <slot></slot>
  </button>
</template>

<script setup>
defineProps({
  type: {
    type: String,
    default: 'default', // 支持 default, primary, danger 等类型
    validator: (value) => ['default', 'primary', 'danger'].includes(value),
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(['click']);

const handleClick = (event) => {
  if (!props.disabled) {
    emit('click', event);
  }
};
</script>

<style scoped>
.my-button {
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.my-button--default {
  background-color: #f0f0f0;
  color: #333;
}

.my-button--primary {
  background-color: #007bff;
  color: #fff;
}

.my-button--danger {
  background-color: #dc3545;
  color: #fff;
}

.my-button--disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>