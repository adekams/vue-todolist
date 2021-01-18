<template>
    <div id="todo-list">
        <h2>My todo list</h2>

        <ul>
            <li v-for="todo in todos" :key="todo.id">
                <todo :todo="todo" 
                    @delete-todo="$emit('delete-todo', todo.id)"
                />
            </li>
        </ul>       
    </div>
</template>

<script>
import todo from './Todo';

export default {
    name: "todolist",
    components: {
        todo
        
    }, 
    props: [
        "todos"
    ]
}
</script>

<style scoped>
    #todo-list {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        position: relative;
    }

    ul li {
        list-style-type: none;
        margin: 50px 0;
        align-items: center;
    }
</style>