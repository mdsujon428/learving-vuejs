<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label >Task</label>
      <input 
      id="task"
      type="text" 
      name="text" 
      v-model="text"
      placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Date & Time</label>
      <input 
      type="reminder" 
      name="day" 
      v-model="day"
      placeholder="Add Date & Time" />
    </div>
    <div class="form-control form-control-check">
      <label for="reminder">Set Reminder</label>
      <input 
      id="reminder"
      type="checkbox"
      v-model="reminder"
      name="reminder" />
    </div>
    <div class="form-control">
      <input 
      type="submit" 
      value="Save Task" 
      class="btn btn-block" />
    </div>
  </form>
</template>

<script>
  export default {
      name:'AddTask',
      data(){
         return{
             text:'',
             day:'',
             reminder:false
         }
      },
      methods:{
        onSubmit(e){
          e.preventDefault()
          if(!this.text){
            alert("Please add a task")
          }
          const newTask = {
            id: Math.floor(Math.random() * 100000),
            text:this.text,
            day:this.day,
            reminder:this.reminder
          } 
            e.target.reset();
            if(!newTask){
               this.$emit('add-task',newTask)
            }
           
        }
      }
  }
</script>

<style scoped>
.add-form{
    margin-bottom: 40px;
}
.form-control{
    margin: 20px 0;
}
.btn{
  background:green;
}
.form-control label{
    display: block;
}
.form-control input{
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}
.form-control-check{
    display: flex;
    align-items:center;
    justify-content: space-between;
}
.form-control-check label{
    flex: 1;
}
.form-control-check input{
    flex: 2;
    height: 20px;
}
</style>