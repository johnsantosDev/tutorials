<script setup>
import { reactive } from "vue"; 
import TodoButton from '../components/TodoButton.vue';
const emit = defineEmits([
"create-todo"
]);
const todoState = reactive({
  todo: "",
  invalid: null,
  errMessage: "",
});
// const todostate =  reactive({
//   todo: "Test...",
// }); 
const createTodo = () => {
  if (todoState.todo != ""){
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    todoState.errMessage = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMessage = "Todo value cannot be enmpty";
}
</script>

<template>
<div class="input-wrap" :class="{ 'input-err' : todoState.invalid}">
    <input type="text" v-model="todoState.todo">
    <TodoButton @click="createTodo()" />
</div>
<p v-show="todoState.invalid" class="err-msg">{{ todoState.errMessage }}</p>
</template>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &.input-err {
    border-color: red;
  }

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }
}

.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}
</style>