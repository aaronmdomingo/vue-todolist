<template>
    <div>
        <div class="input">
            <input type="checkbox" v-on:change="markComplete" :checked="todo.completed">
        </div>
        <div class="text">
            <h2 v-bind:class="{'isCompleted': todo.completed}">{{todo.title}}</h2>
        </div>
        <div class="button">
            <button @click="$emit('deleteTodo', todo.id)">x</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>

div {
    height: 5rem;
    display: flex;
    justify-content: center;
    align-items: center;
}

.input {
    height: 100%;
    width: 20%;
}

.text {
    height: 100%;
    width: 70%;
}

.button {
    height: 100%;
    width: 10%;
}

.isCompleted {
    text-decoration: line-through;
}

button {
    height: 2rem;
    width: 2rem;
    border-radius: 50%;
    color: white;
    background-color: red;
}


</style>