<template>
    <div>
        <ul>
            <!-- todoItems는 props-->
            <li v-for="(item, index) in todoItems " :key="index">{{item}}</li>
        </ul>
    </div>
</template>

<script>

    export default {
        props:['todoItems'],
        setup(){
            
        }
    }
</script>

<style lang="scss" scoped>

</style>