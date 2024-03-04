<template>
    <div>
        <ul>
            <!-- todoItems는 props-->
            <li v-for="(item, index) in todoItems " :key="index">
                <span>
                    {{item}} 
                </span>
                <!-- v-for에 있는 item, index-->
                <button @click="removeTodo(item,index)">삭제</button>
            </li>
        </ul>
    </div>
</template>

<script>

    export default {
        props:['todoItems'],
        setup(props,context){
            function removeTodo(item, index){
                context.emit('remove',item,index);
            }

            return{ removeTodo }
        }
    }
</script>

<style lang="scss" scoped>

</style>