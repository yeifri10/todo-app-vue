<template>
    <div class="container mx-auto px-4 py-20 flex flex-col flex-wrap">
        <h1 class="font-hairline text-6xl text-center text-gray-3  00">Y & Y</h1>

        <todo-card class="mx-auto mt-4 h-54 w-1/2   flex content-start flex-wrap  bg-gray-100 ">

             
                    
            
                    <form class="w-full max-w-sm mx-40">
                        

                                
                                    <div class="mb-4">
                                    

                                     <input class="appearance-none  bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="Name Project" aria-label="Full name">
                                   <hr>
                                    <input v-model="newTask" v-on:keyup.enter="addTask()" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Task" >
                                    
                                    </div>
                                   
                                    <div class="flex items-center justify-between">
                                   
                                    

                                <button @click="addTask()"  class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="button">
                                     Create
                                </button>

                                <button @click="clearCompleted()" class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="button">
                                     Completed
                                </button>


                                <button @click="clearAll()" class="flex-shrink-0 bg-teal-500 border border-teal-500 hover:bg-red-400   text-sm border-4 text-white py-1 px-2 rounded" type="button">
                                     Clear All
                                </button>
                        </div>
                    </form>

        </todo-card>

        <todo-card v-if="tasks.length > 0"  id="task-item"  class="mx-auto mt-4 h-54 w-1/2   flex content-start flex-wrap  bg-gray-100 ">
            <ul id="tasks__item">
                <li v-for="task in tasks" :key="task.id" class="priority" :class="{strikeout:task.done}" @click="taskDone(task)">{{tasks.title}}
                   <div  class="flex mx-40">   
                        <button :class="{'line-through': task.done}" class="task_item_toggle task_item_toggle--completeed shadow appearance-none border rounded w-auto py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username"  type="text" placeholder="Task" >
                        
                        {{ task.title }}
                        </button>
                        <button @click="removeTask(index)" class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="button">
                                                Delete
                        </button>
                        <button @click="taskDone(task)" class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="button">
                                                Done
                        </button>
                     </div>
                     <hr>
               </li>
            
            </ul>
           
        </todo-card>

        <todo-card class="mx-auto mt-4 h-54 w-900   flex content-start flex-wrap  bg-gray-100 p hover:bg-teal-700 rounded-full py-2 px-4" >
             <button class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="button">
                                    + New List +
             </button>
            
        
        </todo-card>

        

        
           
            
       
    </div>
</template>

<script>
export default {
    props: {

    },
 
    data () {
        return {
            newTask: '',
            tasks: []
        };
    },

    mounted () {

    },

    methods: {
        addTask() {
        
            this.tasks.push({
            title: this.newTask,
            done: false
            });
            this.newTask = '';
         
       } ,
            clearAll() {
            this.tasks = [];
            },
            removeTask(index) {
            this.tasks.splice(index, 1);
            },
            clearCompleted() {
            this.tasks = this.tasks.filter(this.inProgress);
            },
            taskDone (task){
                    task.done = !task.done;
            }

    
    }
}

       
</script>