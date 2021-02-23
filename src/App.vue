<template>
    <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput v-on:addTodoEvent="addTodo"></TodoInput>
      <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
      <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
    </div>
</template>
<script>
import TodoHeader from './compoments/TodoHeader.vue'
import TodoInput from './compoments/TodoInput.vue'
import TodoList from './compoments/TodoList.vue'
import TodoFooter from './compoments/TodoFooter.vue'

export default {
  data() {
    return {
        todoItems: []
    }
  },
  created: function() {
        if (localStorage.length > 0) {
            for (var i = 0; i < localStorage.length; i++) {
              if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
                this.todoItems.push(localStorage.key(i));
              }
            }
        }
  },
  methods: {
    addTodo: function(todoItem) {
      // 다른 컴포넌트에서 이걸 호출할거임
      // 매핑은 템플릿에 작성
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo: function(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAll: function() {
      localStorage.clear();
      this.todoItems = [];
    },
  },
  components: {
      'TodoHeader': TodoHeader,
      'TodoInput': TodoInput,
      'TodoList': TodoList,
      'TodoFooter': TodoFooter
    }
}
</script>
<style>
    body {
      text-align: center;
      background-color: #F6F6F8;
    }
    input {
      border-style: groove;
      width: 200px;
    }
    button {
      border-style: groove;
    }
    .shadow {
      box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
    }
</style>