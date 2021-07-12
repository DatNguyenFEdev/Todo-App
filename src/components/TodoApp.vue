<template>
  <div id="todoapp">
      <h1>TODO APP</h1>
      <div class="input-todo">
          <input type="text" 
          v-model="todo"
          @keypress.enter="addTodo"
          >
          <button @click="addTodo">
              <i class="fas fa-plus btn-plus"></i>
          </button>
      </div>
      <ul class="view-todos">
          <li v-for="(todo,index) in todos" :key="index">
              <div :class="{status :completed}" @dbclick="statusTodo(index)"> {{todo.name}} </div>
              <div @click="deleteTodo(index)">
                  <i class="fas fa-trash btn-delete"></i>
              </div>
              <div @click="editTodo(index)">
                  <i class="fas fa-edit btn-trash"></i>
              </div>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
    // props: {msg: String},
    data() {
        return {
            completed: false,
            edit: null,
            todo: '',
            todos: [
               
            ]
    }
},
    methods: {
        addTodo() {
            if(this.todo.trim()=== '')
            return;
            if(this.edit === null) {
                this.todos.unshift(
                {
                    name: this.todo,
                    completed: false
                }
            );
            }
            else {
                this.todos[this.edit].name = this.todo;
                this.edit = null;
            }
            this.todo = '';
        },
        deleteTodo(index) {
            this.todos.splice(index,1);
        },
        editTodo(index) {
            this.todo = this.todos[index].name;
            this.edit = index;
        },
        statusTodo(index) {
            this.todos[index].completed = !this.completed;
            console.log(!this.completed);
        }
}
}
</script>

<style scoped>

#todoapp {
    padding: 20px 0;
    width: 600px;
    height: 460px;
    background: linear-gradient(to bottom right, red, yellow);
    margin:0 auto;
    color: white;
    text-align: center;
    border-radius: 20px;
}
.input-todo {
    text-align: center;
    margin-bottom: 20px;
}

input {
    width: 300px;
    border-radius:10px 0 0 10px;
}

button {
    border-radius:0 10px 10px 0;
}

input, button{
    padding: 10px 20px;
    outline: none;
    border: none;
    font-weight: bold;
}
button:hover{
    background: #999;
    transition: linear 0.4s;
    color: white;
}

.view-todos {
    display: inline-block;
    text-align: center;
    margin: 0 auto;
}

 ul {
    width: 500px;
    max-height: 310px;
    overflow-y:scroll;
    margin: 0 auto;
 }
li {
    width: 500px;
    max-width: 500px;
    list-style: none;
    margin: 0 auto 20px auto;
    border-bottom: 1px solid #999;
    position: relative;
    display: flex;
    text-align: left;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
li >div {
    display: inline-block;
    margin-left: 20px;
    color: blue;
}
.status {
    text-decoration: line-through;
}
li >div:first-child {
    display: inline-block;
    width: 400px;
    max-width: 400px;
    cursor: pointer;
}
.btn-delete, .btn-trash {
    position: absolute;
    top: 0;
}
/* .bnt-plus {

} */
.btn-trash {
    right: 40px;
}
.btn-delete {
    right: 0;
    color: red;
}
i, button{
    cursor: pointer;
}
::-webkit-scrollbar {
    display: none;
}
</style>