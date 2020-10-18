<template>
    <li>
        <span v-bind:class="{ done:todo.completed }">
            <label class="checkbox_label" v-on:change="todo.completed = !todo.completed">
                <input type="checkbox" class="checkbox_input">
                <strong>{{ todo.id }}</strong>
                {{ todo.title }}
            </label>
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    }
}
</script>

<style lang="css" scoped>

li {
    padding: .5rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 2px solid #575757;
    margin: 1rem 0;
    background: #f7f7f7;
}

.rm {
    background: #b13434;
    padding: 1px 6px;
    color:#f7f7f7;
    border: none;
    font-size: 19px;
    outline: none;
    cursor: pointer;
}

.rm:hover {
    background: #772222;

}

.done {
    text-decoration: line-through;
}

input {
    margin-right: 1rem;
}

/* <checkbox/>======================================== */


.checkbox_input {
    /* width: 20px;
    height: 20px; */
}

.checkbox_label {
    cursor: pointer;
    -moz-user-select: none;
    -webkit-user-select: none;
    user-select: none;
}
    
</style>