<template>
    <div v-bind:class="{'is-complete':todo.completed}">
        <p><input type="checkbox" v-on:change="markComplete">{{todo.title}}</p>
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
   .is-complete {
       color: lightgray
   }

   .del {
       border-radius: 10px;
       background-color: red;
       border: none;
       box-shadow: 5em;
   }
</style>