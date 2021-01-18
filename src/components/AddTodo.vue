<template>
    <div>
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title">
            <button type="submit" id="add">Add</button>
        </form>
    </div>
</template>

<script>
import {v4} from "uuid";

export default {
    name: "AddTodo",
    data() {
        return {
            title: '',
        }
    },
    methods: {
        addTodo() {
            const uuid = v4()

            const newTodo = {
                
                id: uuid,
                title: this.title,
                completed: false
            }
            if(this.title) {
                this.$emit( "add-todo", newTodo);
            }else{
                alert("todo cannot be empty")
            }
            this.title = ''
        },
    },
}
</script>

<style>
    form {
        margin: 40px 0;
        text-align: center;
        display: flex;
        justify-content: center;
        width: 300px;
        margin: auto;
    }

    input[type='text'] {     
        box-sizing: border-box;
        border-radius: 5px 0px 0px 5px;
        border: 1px solid #282828;
        border-right-color: transparent;
        font-size: 18px;
        padding: 10px 8px;
        width: 70%;
    }
    #add {     
        background: #282828;
        border: 1px solid transparent;
        box-sizing: border-box;
        border-radius: 0 5px 5px 0;
        color: white;
        font-weight: 600px;
        font-size: 18px;
        padding: 10px 15px;
    }

    input:focus, button:focus {
        outline: none;
    }

    button:hover {
        cursor: pointer;
        opacity: .6;
    }
</style>