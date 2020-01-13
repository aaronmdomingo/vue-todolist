<template>
    <div class="search__container">
        <input type="text" placeholder="Search Here" v-model="name">
    </div>
</template>

<script>
export default {
    name: "TodoSearch",
    data() {
        return {
            name: ''
        }
    },
    watch: {
        name: function() {
            this.$emit('searchTodo', this.name);
        }
    }
}
</script>

<style scoped>
.search__container {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

input {
    width: 80%;
    height: 50%;
    text-align: center;
    border: 2px solid black;
}


</style>
