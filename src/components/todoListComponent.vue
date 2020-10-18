<template>
    <div class="todoComponent">
        <ul>
            <todoItemComponent
                v-for="todo of todos"
                v-bind:key="todo.id"
                v-bind:todo="todo"
                v-on:remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>

<script>

import todoItemComponent from '@/components/todoListItemComponent'

export default {
    props: ['todos'],
    components: {
        todoItemComponent
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id);
        }
    },
    
}
</script>

<style lang="css" scoped>
    .todoComponent {
        width: 40%;
        margin: 0 auto;
        padding: 20px;
        background: #abf8d2;
        border-radius: 20px;
        text-align: justify;
    }
    h1 {
        text-align: center;
    }
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>