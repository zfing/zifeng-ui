<template>
  <div>
    <Button type="primary" @click="handleClick">Primary Button</Button>
    <Button type="danger" disabled>Disabled Button</Button>
  </div>
</template>

<script setup>
import { Button } from './components';

const handleClick = () => {
  alert('Button clicked!');
};
</script>