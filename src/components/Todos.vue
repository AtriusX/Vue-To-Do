<template>
    <div class="container">
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" 
                v-on:update-todo="$emit('update-todo', todo)" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem'
export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>
    .container {
        background-color: whitesmoke;
        border-radius: 15px;
        margin: 10px 0;
        padding: 0 15px;
    }
</style>