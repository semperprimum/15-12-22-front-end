<template>
  <header>
    <h1>{{title}}</h1>
    <Button @toggle-add-product='$emit("toggle-add-product")' text='Добавить товар' color="green"/>
  </header>
</template>

<script>
import Button from './Button.vue';

export default {
  components: { Button },
  name: 'Header',
  props: {
    title: {
      type: String,
      default: 'Учет Товаров',
    },
    components: {
      Button
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>