<template lang="">
    <div>
        <form @submit ='addTodo'>
        <input type='text' v-model='todo'  placeholder="Add Todo.."/>
        <input type='submit' class ="btn-green " value="Add">

        </form>
        <ul>
            <div class="todoItem" v-for='(todo,index) in todoList' :key ='index'>
                <div class='title'>
                 <span :class="{ 'task-done': todo.isCompleted }">
                     <strong>{{todo.title}}</strong>
            </span>
                
                </div>
                <div class='status' >
                    <p :class="{'completed' : todo.isCompleted,'incomplete':!todo.isCompleted}">{{todo.isCompleted? "Completed" : "Incomplete"}}</p>
                </div>
                <div class='controls'>
                    <a href="#" class="complete-item item-icon" @click="completeTodo(index)"><i class="far fa-check-circle"></i></a>
       <a href="#" class="edit-item item-icon" @click="editTodo(index)"><i class="far fa-edit"></i></a>
       <a href="#" class="delete-item item-icon" @click="deleteTodo(index)"><i class="far fa-times-circle"></i></a>
                </div>
                </div>

        </ul>
        <button class ="btn-green clear" @click="clearTodo(this)">Clear</button>
    </div>
</template>
<script>

export default {
    
    name: 'AddInput',
    data() {
        return {
            todo: "",
            todoList: []
        }
    },
    created() {
    if (localStorage.getItem('todoList')) {
      try { 
        this.todoList = JSON.parse(localStorage.getItem('todoList'));
        console.log(this.todoList)
      } catch(e) {
        localStorage.removeItem('todoList');
      }
    }
  },
    methods: {
        addTodo: function (e) {
            e.preventDefault();
            if(this.todo == ""){
                return 0;
            }
            let todo = {
                title: this.todo,
                isCompleted: false, 
            }
            this.todoList.push(todo);
            this.todo = '';
            this.saveLocal()
        },
        completeTodo: function (index) {
            this.todoList[index].isCompleted = !this.todoList[index].isCompleted
        },
        editTodo: function (index) {
            this.todo = this.todoList[index].title;
            this.todoList = this.todoList.filter((todo, ind) => ind == this.index);
        },
        deleteTodo : function () {
            this.todoList = this.todoList.filter((todo, ind) => ind == this.index);
        },
        saveLocal : function(){
            const listString = JSON.stringify(this.todoList);
            localStorage.setItem('TodoList', listString);
        },
        clearTodo : function () {
            this.todoList = [];
        }
    }
}



</script>
<style scoped >
    ul{
        list-style-type: none;
    }
    .task-done {
  text-decoration: line-through;
  text-decoration: line-through;
        opacity: 0.5;
}
    .todoItem{
        display: flex;
    }
    .completed{
        color: #25c060;
    }
    .incomplete{
        color:#d62828;
    }
    .todoItem .title{
        width: 55%;
        margin: 16px;
        text-align: left;
    }
    .todoItem .status{
        text-align: left;
        width: 100px;
        font-size: 14px;
        padding: 5px;
    }
    .item-icon {
        font-size: 1.2rem;
        cursor: pointer;
    }
    .complete-item:hover {
        color: #25c060;
    }
    .edit-item:hover {
        color: #11b5e4;
    }
    .delete-item:hover {
        color: #d62828;
    }
    .btn-green {
        background: transparent;
        color: #25c060;
    }
    .btn-green:hover {
        background:#25c060;
        color: #232323;
    }
    .controls{
        margin: 16px;
    }

    .controls a{
        padding: 0 10px;
    }
    .clear{
        padding: 8px 20px;
        border-radius: 5px;
    }
    input{
        padding: 8px;
        border-radius:5px;
        outline: none;
    }
    input[type='text']{
        width: 80%;
        border-top-right-radius: 0px;
        border-bottom-right-radius: 0px;
    }
    input[type='submit']{
        width: 12%;
        border-top-left-radius: 0px;
        border-bottom-left-radius: 0px;
        
    }
</style>