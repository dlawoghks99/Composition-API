<template>
  <TodoHeader></TodoHeader>
  <TodoInput></TodoInput>
  <!-- :하위Props명칭 = 내려보내줄 배열 -->
  <todoList :todoItems="todoItems"></todoList>
</template>

<script>
import { ref } from 'vue';
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

  export default {
  components: { TodoHeader,TodoInput, TodoList },
    setup(){
      const todoItems = ref([]);

      // localstorage 아이템을 반환한다.
      function fetchTodos(){
        const result = [];

        for(let i = 0; i < localStorage.length; i++){
            const todoItem = localStorage.key(i);
            // items.value.push(todoItem);
            result.push(todoItem);
        }

        return result;
      }
            
      todoItems.value = fetchTodos();

      return { todoItems };
    }
  }
</script>

<style lang="scss" scoped>

</style>