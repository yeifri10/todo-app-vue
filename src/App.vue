<template>
    <div id="app" class="bg-teal-500 bg-cover">
       

        <HelloWorld/>
        <TodoList/>
       

    </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import HelloWorld from './components/HelloWorld.vue'


export default {
    name: 'app',
    components: {
        TodoList,
        HelloWorld

    }
}
</script>