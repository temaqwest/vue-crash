<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit" class="add">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
        }
    },
    methods: {
        onSubmit() {
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false,
                }
                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    },
}
</script>

<style lang="css" scoped>

form {
    display: flex;
    margin: 0 auto;
    width: 500px;
}

input {
    width: 400px;
    margin: 0 20px;
    background: #f7f7f7;
    border: none;
    outline: none;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

.add {
    background: #34b134;
    padding: 4px 16px;
    color:#f7f7f7;
    border: none;
    font-size: 19px;
    outline: none;
    cursor: pointer;
}

.add:hover {
    background: #237723;
}
    
</style>