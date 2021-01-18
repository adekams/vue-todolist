<template>
    <section>
        <div :class="{ 'completed': todo.completed }">
            <p id="todo-item">
                {{ todo.title }}
                <input @click="markComplete" type="checkbox" name="" id="check">
                <span class="checkbox-custom"></span>
                
            </p>
            
        </div>

        <button 
            @click="$emit('delete-todo', todo.id)" id="trash">&times;
        </button>
    </section>
    
</template>

<script>
export default {
    name: "Todo",
    props: [
        "todo"
    ],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .completed {
        text-decoration: line-through green 2px;
    }

    section {
        position: relative;
        display: flex;
        justify-content: space-evenly;
        align-content: center;
        font-size: 18px;
        margin: 20px auto;
        width: 100%;
    }

    #todo-item {
        margin: 0 auto;
    }

    #trash {
        font-size: 20px;
        font-weight: 600;
        color: #fff;
    }

    /* making and styling a custom checkbox */

    /* default checkbox */
    #check {
        opacity: 0;
        position: absolute;
        cursor: pointer;
        left: 0; 
        top: 0; 
        height: 20px;
        width: 20px;
    }
    
    /* custom checkbox */
    .checkbox-custom {
        position: absolute;
        top: 0;
        left: 0;
        height: 25px;
        width: 25px;
        border: 1px solid #282828;
        background: #eee;
        border-radius: 5px;
        z-index: -1;
    }

    /*custom indicator unchecked */
    .checkbox-custom::after {
        content: '';
        position: absolute;
        display: none;
    }

    /* custom checkbox when checked */
    #todo-item input:checked ~ .checkbox-custom {
        background: green;
    }

    /* when checked, show */
    #todo-item input:checked ~ .checkbox-custom::after {
        display: block;
    }

    /*custom indicator when checked*/
    #todo-item .checkbox-custom::after {
        width: 7px;
        height: 13px;
        margin-left: 6px;
        margin-top: 2px;
        border: solid white;
        border-width: 0 3px 3px 0;
        transform: rotate(45deg);
    }

    button {
        text-align: bottom;
        background: red;
        color: #fff;
        border: 1px solid #ccc;
        height: 30px;
        padding: 0px 10px;
        border-radius: 5px;
        box-sizing: border-box;
        
    }

</style>