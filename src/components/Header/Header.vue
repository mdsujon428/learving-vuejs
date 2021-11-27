<template>
  <header>
      <h1>{{title}}</h1>
      <Button 
      @btn-click="$emit('toggle-add-task')" 
      :text="showAddTask ? 'Close' : 'Add Task'" 
      :color="showAddTask ? 'red' : 'green'"/>   
  </header>
</template>
<script>
import Button from '../Buttons/Button.vue';
export default {
    name:'Header',
    props:{
        title:{
            type:String,
            showAddTask:Boolean
        }
    },
    components:{     
            Button
    },
    // methods:{
    //     hello(showAddTask){
    //         console.log(showAddTask)
    //     }
    // }
}

</script>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items:center ;
        margin-bottom: 20px;
    }
</style>