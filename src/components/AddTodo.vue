<template>
    <form @submit="addTodo">
        <input type="text" v-model="title" name="title" placeholder="Add Todo..." autocomplete="off"/>
        <input type="submit" value="Submit" class="btn"/>
    </form>
</template>
<script>
    export default {
        name: "AddTodo",
        data() {
            return {
                title: ''
            }
        },
        methods: {
            addTodo(e){
                e.preventDefault();
                if (this.title === '')
                    return;
                const newTodo = {
                    title: this.title,
                    completed: false
                };
                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    }
</script>
<style scoped>
    form {
        display: flex;
    }
    input[type="text"] {
        flex: 10;
        padding: 5px;
    }
    input[type="submit"] {
        flex: 2;
    }
    .btn {
        display: inline-block;
        border: none;
        background: #555;
        color: #fff;
        padding: 7px 20px;
        cursor: pointer;
    }
    .btn:hover {
        background: #666;
    }
</style>