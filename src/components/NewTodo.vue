<template>
   <form @submit.prevent="addTodo">
        <input type="text"
               placeholder="todo"
               v-model="newTodo.title"
               autoFocus/>
    </form>
</template>

<script>
    export default {
        props: ['addTodo', 'newTodo']
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    form input {
        border-bottom: 4px solid black;
    }

</style>
