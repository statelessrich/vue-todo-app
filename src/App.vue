<template>
  <section id="app" class="app-container">
        <new-todo v-bind:newTodo="newTodo" :addTodo="addTodo"></new-todo>
        <todo-list v-bind:todos="todos" :deleteTodo="deleteTodo"></todo-list>
  </section>
</template>

<script>
    import TodoList from './components/TodoList';
    import NewTodo from './components/NewTodo';

    export default {
        name: 'app',
        components: {
            TodoList,
            NewTodo
        },
        methods: {
            /**
             * Delete todo item at given index.
             * @param {number} index Index of todo item to delete.
             */
            deleteTodo: function(index) {
                this.todos.splice(index, 1);
            },

            /**
             * Adds new todo to list.
             */
            addTodo: function() {
                if (!this.newTodo.title) {
                    return;
                }
                this.todos.push(this.newTodo);

                // Reset new todo.
                this.newTodo = {
                    title: '',
                    done: false,
                    mouseover: false
                };
            }
        },
        data() {
            return {
                newTodo: {
                    title: '',
                    done: false,
                    mouseover: false
                },
                todos: []
            }
        },

    }

</script>

<style>
    .app-container {
        display: flex;
        width: 100%;
        height: 100%;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    
    todo-list {
        margin: auto;
    }
    
    body,
    html,
    #root {
        height: 100%;
        width: 100%;
    }
    
    body {
        margin: 0;
    }
    
    html {
        overflow-x: hidden;
        overflow-y: auto;
    }
    
    input {
        font-size: 5vw;
        border: none;
        outline: none;
        font-family: 'Roboto Mono', monospace;
    }

</style>
