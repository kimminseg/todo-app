<template>
  <div>
    <todo-header></todo-header>
    <todo-input v-on:add="addItem"></todo-input>
    <todo-list
      v-bind:propsData="todoItems"
      v-on:remove="removeItem"
    ></todo-list>
    <todo-footer v-on:clear="clearItems"></todo-footer>
    <!-- TODO: TodoInput, TodoList 컴포넌트 등록 -->
  </div>
</template>
<script>
// import 컴포넌트 이름 from '컴포넌트 파일 경로';
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  components: {
    // '컴포넌트 이름': 컴포터는 내용,
    'todo-header': TodoHeader,
    'todo-input': TodoInput,
    'todo-list': TodoList,
    'todo-footer': TodoFooter,
  },
  data() {
    return {
      todoItems: [],
      inputText: '',
    };
  },
  methods: {
    fetchTodoItems: function() {
      for (var i = 0; i < localStorage.length; i++) {
        var value = localStorage.key(i);
        this.todoItems.push(value);
      }
    },
    clearItems: function() {
      this.todoItems = [];
      localStorage.clear();
    },
    addItem: function(inputText) {
      localStorage.setItem(inputText, inputText);
      this.todoItems.push(inputText);
    },
    removeItem: function(todoItem, index) {
      // 배열 변경
      this.todoItems.splice(index, 1);
      // 브라우저 저장소에서 삭제
      localStorage.removeItem(todoItem);
    },
  },
  created: function() {
    this.fetchTodoItems();
  },
};
</script>

<style></style>
