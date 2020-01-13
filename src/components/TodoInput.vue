<template>
    <form class="input__container" @submit="addTodo">
        <div class="input__text">
            <input type="text" v-model="name" name="title" placeholder="Add Todo..." autocomplete="off">
        </div>
        <div class="input__button">
            <button type="submit">
                Submit
            </button>
        </div>
    </form>
</template>

<script>
export default {
    name: "TodoInput",
    data() {
        return {
            name: ''
        }
    },
    methods: {
            addTodo(event) {
                event.preventDefault();
                const newTodo = {
                    id: Math.random() * 1000,
                    title: this.name,
                    completed: false
                }
                this.$emit('addTodo', newTodo);
                this.name = '';
            }
        }
}
</script>

<style scoped>
.input__container {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center
}

.input__text,
.input__button {
    height: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.input__text {
    width: 70%;
}

input {
    height: 70%;
    width: 70%;
    text-align: center;
}

.input__button {
    width: 30%;
}

button {
    border-radius: 5px;
    height: 2rem;
    width: 7rem;
    color: white;
    background-color: #428bca;
}


</style>