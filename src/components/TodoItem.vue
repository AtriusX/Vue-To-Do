<template>
    <div v-bind:class="{'is-complete':todo.completed}">
        <p><input type="checkbox" v-on:change="markComplete"> {{todo.title}}</p>
        <button @click="$emit('del-todo', todo.id)" class="del">x</button>
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
        display: flex;
        padding: 5px;
    }

   .is-complete {
       color: lightgray;
       font-style: italic;
    }

    p {
        flex: 9;
        font-size: 1.2rem;
    }

    input[type="checkbox"] {
        color: skyblue;
        margin-right: 2px;
    }

   .del {
       flex: 0.3;
       border-radius: 10px;
       background-color: #fd2c2c;
       border: none;
       color: white;
       box-shadow: 5em;
       margin: 15px 0;
   }

   .del:active {
        background: gray;
    }

    .del:hover {
        background: #ff5959;
    }
</style>