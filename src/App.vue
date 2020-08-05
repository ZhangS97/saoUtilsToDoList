<template>
  <div id="app">
    <div class="container">

      <section>
        <div class="row justify-content-center mt-4">
          <input
            v-model="inputField"
            v-on:keyup.enter="addTodo"
            class="mr-1"
            placeholder="Todo Item"
          />
          <button
            @click="addTodo"
            class="btn btn-primary"
          >Add Todo</button>
        </div>
      </section>

      <section class="container">
        <div class="row">
          <div class="offset-md-3 col-md-6 mt-3">
            <ul class="list-group justify-content-center">
              <li
                class="row list-group-item border mt-2 col-xs-1"
                v-for="todo in todoList"
                :key="todo.id"
              >
                <div class="row align-items-center">
                  <input
                    type="checkbox"
                    v-on:change="toggle(todo)"
                    v-bind:checked="todo.complete"
                    class="col-sm-1 border border-danger"
                  >
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
                  <span
                    @click="deleteTodo(todo)"
                    class="offset-sm-1 col-sm-2 delete text-right"
                  >X</span>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </section>

    </div>
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
