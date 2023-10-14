<template>
  <ul class="todo-list">
    <AppTodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :todo="{
        id: index,
        text: todo.text,
        completed: todo.completed,
      }"
    />
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AppTodoItem from './AppTodoItem.vue';
import { Todo } from '@/types/Todo';

interface State {
  todos: Todo[];
}

export default defineComponent({
  components: {
    AppTodoItem,
  },
  data(): State {
    return {
      todos: [
        {
          id: 0,
          text: 'Learn the basics of Vue',
          completed: true,
        },
        {
          id: 1,
          text: 'Learn the basics of Typescript',
          completed: false,
        },
        {
          id: 2,
          text: 'Subscribe to the channel',
          completed: false,
        },
        {
          id: 3,
          text: 'Learn the basics of JS',
          completed: true,
        },
      ],
    };
  },
});
</script>
