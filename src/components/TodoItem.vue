<template>
     <!-- We are binding a CSS class on the condition that todo.completed field is true -->
    <div class="todo_item" v-bind:class="{'is_complete':todo.completed}">
        <input type="checkbox" v-on:change="markComplete">
        <p>{{todo.title}}</p>
        <button @click="$emit('del-todo',todo.id)" class="del">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete(){
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo_item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is_complete{
        text-decoration: line-through;
    }

    .del{
        background: red;
        color: #ffff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        
    }
</style>