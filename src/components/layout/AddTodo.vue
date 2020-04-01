<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import uuid from 'uuid'
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            if (this.title === '') 
                return;
            const n = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', n);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        margin-top: 5px;
        padding: 5px;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
        padding-left: 10px;
        border: none;
        background: lightgray;
        color: black;
        border-radius: 100px 0 0 100px;
    }

    input[type="submit"] {
        flex: 1;
        background: #6392d8;
        color: white;
        border: none;
        border-radius: 0 100px 100px 0;
    }

    input[type="submit"]:hover {
        background: lightskyblue;
    }

    input[type="submit"]:active {
        background: lightskyblue;
    }
</style>