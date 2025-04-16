<script setup>
import { uid } from 'uid';
import { Icon } from '@iconify/vue';
import TodoCreator from '@/components/TodoCreator.vue';
import { ref, watch, computed } from 'vue';
import TodoItem from '@/components/TodoItem.vue';



const setTodoListLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
}

const date = new Date();

const todoList = ref([]);


const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
    time: date.getMonth() + 1 + "/" + date.getDate(),
  })
}


watch(todoList, () => {
  setTodoListLocalStorage();
}, {
  deep: true,
})


const todoCompleted = computed(() => {
  return todoList.value.every((todo) => todo.isCompleted);

})


const fetchTodoList = () => {
  const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
  if (savedTodoList) {
    todoList.value = savedTodoList;
  }
};

fetchTodoList();



const toggleTodoComplete = (todoPos) => {
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
  todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
  todoList.value[todoPos].todo = todoVal;
}

const deleteTodo = (todoId) => {
  todoList.value = todoList.value.filter((e) => e.id !== todoId)
}

</script>

<template>
  <main>
    <h1>Create Todo</h1>
    <TodoCreator @create-todo="createTodo" />
    <ul class="todo-list" v-if="todoList.length !== 0">
      <!-- vue的語法糖，template內都會自動抓todoList.value -->
        <TodoItem v-for="(todo, index) in todoList" :todo="todo" :index="index" @toggle-complete="toggleTodoComplete"
          @edit-todo="toggleEditTodo" @update-todo="updateTodo" @delete-todo="deleteTodo" />
    </ul>
    <p class="todos-msg" v-else>
      <Icon icon="noto-v1:sad-but-relieved-face" width="22" height="22" />
      <span>哎呀！代辦事項呢？趕快寫！</span>
    </p>
    <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">
      <Icon icon="noto-v1:party-popper" width="50" height="50"  />
    <span>You have completed all your todos! <br />你完成所有項目了，好棒！</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>
