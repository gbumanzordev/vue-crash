<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      :text="showAddTask ? 'Close' : 'Add Task'"
      @click="$emit('toggle-form')"
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import { Options, Vue } from 'vue-class-component';
import Button from '@/components/Button';

@Options({
  name: 'Header',
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
})
export default class Header extends Vue {}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
