<template>
  <div id="app">
    <el-container>
      <el-header>
        <el-row :gutter="20">
  <el-col :span="18">
    <el-input v-model="inputField"
                    @keyup.enter.native="addTodo"                  
 placeholder="Todo Item"></el-input></el-col>
  
  <el-col :span="6"> <el-button @click="addTodo" type="primary">Add Todo</el-button></el-col>
  
</el-row>
        

  
      </el-header>
      <el-main>
        <el-row :gutter="20"
         v-for="todo in todoList"
                :key="todo.id">
                <el-col :span="6">
                               <input
                    type="checkbox"
                    v-on:change="toggle(todo)"
                    v-bind:checked="todo.complete"
                    class="col-sm-1 border border-danger"
                  >
                </el-col>

<el-col :span="12">
                  <del
                    v-if="todo.complete"
                    class="col-sm-8"
                  >
                    <h5>{{ todo.name }}</h5>
                  </del>
                  <span
                    v-else
                    class="col-sm-8"
                  >
                    <h5>{{ todo.name }}</h5>
                  </span>
                </el-col>



                 <el-col :span="6">
                     <el-button type="success" icon="el-icon-check" @click="deleteTodo(todo)" circle></el-button>
                 </el-col>

        </el-row>
        
      </el-main>

    </el-container>

  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  methods: {
    addTodo: function (todo) {
      todo = this.inputField;
      this.todoList.push({ name: todo, complete: false });
      this.inputField = '';
      console.log(this.todoList);
    },
    deleteTodo: function (todo) {
      var index = this.todoList.indexOf(todo);
      this.todoList.splice(index, 1);
      console.log(this.todoList);
    },
    toggle: function (todo) {
      todo.complete = !todo.complete;
    }
  },
  data() {
    return {
      inputField: '',
      todoList: []
    }
  }


}
</script>

<style>
</style>
