<template>
  <div id="app">
    <el-container>
      <el-header>
        <el-row :gutter="20">
          <el-col :span="18">
            <el-input v-model="inputField" @keyup.enter.native="addTodo" placeholder="今天要做哪些事呢？"></el-input>
          </el-col>

          <el-col :span="6">
            <el-button @click="addTodo" type="primary">添加</el-button>
          </el-col>
        </el-row>
      </el-header>
      <el-main>
          <el-row :gutter="20" v-for="todo in todoList" :key="todo.id">
            <el-col :span="12">
              <del v-if="todo.complete">
                <h5>{{ todo.name }}</h5>
              </del>
              <span v-else>
                <h5>{{ todo.name }}</h5>
              </span>
            </el-col>

            <el-col :span="6">
              <el-button type="primary" @click="deleteTodo(todo)" round>完成</el-button>
            </el-col>

            <el-col :span="6">
              <el-button type="danger" icon="el-icon-delete" @click="deleteTodo(todo)" circle></el-button>
            </el-col>
          </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  methods: {
    addTodo: function (todo) {
      todo = this.inputField;
      this.todoList.push({ name: todo, complete: false });
      this.inputField = "";
      console.log(this.todoList);
    },
    deleteTodo: function (todo) {
      var index = this.todoList.indexOf(todo);
      this.todoList.splice(index, 1);
      console.log(this.todoList);
    },
    toggle: function (todo) {
      todo.complete = !todo.complete;
    },
  },
  data() {
    return {
      inputField: "",
      todoList: [],
    };
  },
};
</script>

<style>

</style>
