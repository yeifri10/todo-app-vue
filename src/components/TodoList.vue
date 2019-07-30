<template>
    <div class="container mx-auto px-4 py-20 flex flex-col flex-wrap">
        <h1 class="font-thin text-6xl text-center text-gray-500">Todo App</h1>

        <todo-card class="mx-auto mt-4 h-64 w-full sm:w-11/12 md:w-5/12">
            Todo List
        </todo-card>

        <todo-card class="mx-auto mt-10 w-full sm:w-11/12 md:w-5/12">
            Create/Edit Task
        </todo-card>
    </div>
</template>

<script>
export default {
    props: {

    },

    data () {
        return {
            tasks: [
                {
                    id: 1,
                    title: 'Example task',
                    done: false
                }
            ]
        };
    },

    mounted () {

    },

    methods: {

    }
}
</script>