<script setup>
import { ref, defineEmits, reactive } from 'vue';
import TodoButton from './TodoButton.vue';

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
    todo: "",
    invalid: null,
    errMsg: "",
});

const createTodo = () => {
    todoState.invalid = null;
    if (todoState.todo !== "") {
        emit("create-todo", todoState.todo);
        todoState.todo = "";
        return;
    }
    todoState.invalid = true;
    todoState.errMsg = "！內容為必填"
};


</script>


<template>
    <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
        <input type="text" v-model="todoState.todo" />
        <TodoButton @click="createTodo">建立</TodoButton>
    </div>
    <p class="err-msg" v-show="todoState.invalid">{{ todoState.errMsg }}</p>
</template>


<style lang="scss" scoped>
.input-wrap {
    display: flex;
    transition: 250ms ease;
    border: 2px solid #41b080;
    border-radius: 10px;
    overflow: hidden;

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
        border-radius: 10px;

        &:focus {
            outline: none;
        }
    }
}

.err-msg {
    margin-top: 6px;
    font-size: 12px;
    text-align: center;
    color: red;
}
</style>