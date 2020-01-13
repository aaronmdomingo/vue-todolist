<template>
    <div class="container">
        <div class="header">
            <h1>
                Vue To-Do-List App
            </h1>
        </div>
        <div class="searchbar">

        </div>
        <div class="body">
            <div v-bind:key="todo.id" v-for="todo in todos" class="todo">
                <TodoItem v-bind:todo="todo" v-on:deleteTodo="$emit('deleteTodo', todo.id)"/>
            </div>
        </div>
        <div class="input">
            <TodoInput v-on:addTodo="addTodo"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem';
import TodoInput from './TodoInput';

export default {
    name: "Todos",
    components: {
        TodoItem,
        TodoInput
    },
    props: ["todos"],
    methods: {
        addTodo(toDoObj) {
            this.$emit('addTodo', toDoObj);
        }
    }
}
</script>

<style scoped>
.container {
    margin: 1rem;
    height: 50rem;
    width: 30rem;
    border: 2px solid black;
    border-radius: 5px;
}

.header {
    height: 10%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.searchbar {
    height: 10%;
}

.body {
    height: 70%;
    overflow-y: scroll;
}

.input {
    height: 10%;
}


</style>