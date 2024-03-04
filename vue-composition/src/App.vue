<template>
  <div>
    <p>{{ message }}</p>
    <button @click="changeMessage">변경</button>
  </div>
</template>

<script>
import {useMessage} from './hooks/useMessage'


export default {
    // data() {
    //     return {
    //         message: 'heelo'
    //     }
    // },
    setup(){
        const {changeMessage,message} = useMessage();

        // const message = ref('hello');

        // function changeMessage(){
        //     message.value = 'hi';
        // }

        return {message, changeMessage}

    },
    // methods:{
    //     changeMessage(){
    //         this.message = 'hi'
    //     }
    // }
}
</script>

<style>

</style>