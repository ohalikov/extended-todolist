<template>
  <AppHeader />
  <AppFilters />
  <main class="app-main">
    <AppTodoList
      :todos="todos"
      @toggle-todo="toggleTodo"
      @remove-todo="removeTodo"
    />
    <AppAddTodo @add-todo="addTodo" />
  </main>

  <AppFooter />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AppHeader from './components/AppHeader.vue';
import AppFilters from './components/AppFilters.vue';
import AppTodoList from './components/AppTodoList.vue';
import AppAddTodo from './components/AppAddTodo.vue';
import AppFooter from './components/AppFooter.vue';
import { Todo } from './types/Todo';

interface State {
  todos: Todo[];
}

export default defineComponent({
  components: {
    AppHeader,
    AppFilters,
    AppTodoList,
    AppAddTodo,
    AppFooter,
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
  methods: {
    addTodo(todo: Todo) {
      console.log(todo);
      this.todos.push(todo);
    },
    toggleTodo(id: number) {
      console.log('4343');
      const targetTodo = this.todos.find((todo: Todo) => todo.id === id);
      targetTodo && (targetTodo.completed = !targetTodo.completed);
    },
    removeTodo(id: number) {
      this.todos = this.todos.filter((todo: Todo) => todo.id !== id);
    },
  },
});
</script>
