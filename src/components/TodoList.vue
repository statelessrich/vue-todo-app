<template>
  <section class="todo-container">      
      <section class="list" v-for="(todo, index) in todos" @mouseover="todo.mouseover=true" @mouseleave="todo.mouseover=false">
           <section class="flex-container">
                <input v-model="todo.done" class="" v-bind:class="{'checkbox': true,'checkbox--visible': todo.mouseover}" type="checkbox" name="done"/>
            </section>

            <input type="text" v-model="todo.title" class="list__item" v-bind:class="{'list__item--done': todo.done}"/>

            <section class="flex-container">
                <a @click="deleteTodo(index)" v-bind:class="{'delete': true, 'delete--visible': todo.mouseover}" href="#">x</a>
            </section>
        </section>
      </section>
</template>

<script>
    export default {
        props: ['todos', 'deleteTodo'],
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .list {
        margin-left: -8vw;
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
    
    .list__item {
        width: 83%;
    }
    
    .list__item--done {
        text-decoration: line-through;
    }
    
    .flex-container {
        display: flex;
        align-items: center;
    }
    /* checkbox */
    
    .checkbox {
        -webkit-appearance: none;
        background-color: #fafafa;
        border: 4px solid #000;
        padding: 2vw;
        display: inline-block;
        position: relative;
        width: 3vw;
        height: 3vw;
        margin-right: 20px;
        visibility: hidden;
    }
    
    .checkbox--visible {
        visibility: visible;
    }
    
    .checkbox:checked:after {
        content: '\2714';
        font-size: 6vw;
        position: absolute;
        top: -2vw;
        left: -0.5vw;
    }
    /* delete button */
    
    .delete {
        font-size: 5vw;
        text-decoration: none;
        font-family: sans-serif;
        color: black;
        visibility: hidden;
    }
    
    .delete--visible {
        visibility: visible;
    }

</style>
