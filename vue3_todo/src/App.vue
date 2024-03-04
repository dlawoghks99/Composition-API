<template>
  <TodoHeader :appTitle="title"></TodoHeader>
  <!--@하위컴퍼넌트 명(add) 상위컴퍼넌트에서 실행할 메서드명-->
  <TodoInput @add="addTodoItem"></TodoInput>
  <!-- :하위Props명칭 = 내려보내줄 배열 -->
  <todoList :todoItems="todoItems" @remove="removeTodoItem"></todoList>
</template>

<script>
import { ref } from 'vue';
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

  export default {
  components: { TodoHeader,TodoInput, TodoList },
    data() {
      return {
        title: '할일 앱'
      }
    },
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

      // Input컴포넌트에서 실행함(추가)
      function addTodoItem(todo){
        todoItems.value.push(todo);
      }

      // List컴포넌트에서 실행함(삭제)
      function removeTodoItem(item, index){
        todoItems.value.splice(index,1);
        localStorage.removeItem(item);
      }

      return { todoItems, addTodoItem, removeTodoItem };
    }
  }
</script>

<style lang="scss" scoped>

</style>