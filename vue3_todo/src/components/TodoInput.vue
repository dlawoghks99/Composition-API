<template>
    <div>
        <input type="text" v-model="todoInput">
        <button @click="addTodo">추가</button>
    </div>
</template>

<script>
import { ref } from 'vue'
    export default {
        setup(props,context){
            //data
            const todoInput = ref('');

            //methods
            function addTodo(){
                const todo = todoInput.value;
                localStorage.setItem(todo, todo);
                // emit할땐 context선언이 필요하다.
                // 메서드명은 add
                context.emit('add',todo);
                clearTodo();
            }

            // inputBox 초기화
            const clearTodo = () => todoInput.value = '';

            return { todoInput, addTodo, clearTodo }
        }
    }
</script>

<style lang="scss" scoped>

</style>