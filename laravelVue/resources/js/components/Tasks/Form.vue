<template>
    <div class="w-full sm:w-8/12 md:w-5/12 p-5 bg-white">
        <h1 class="text-3xl text-center font-bold py-4 text-gray-800">Create tasks</h1>
    
        <form method="POST" @submit.prevent="saveTask">
            <div class="d-block flex px-2 py-4">
                <input type="text" v-model="task"
                placeholder="New Task" name="todo"
                class="text-xl p-2 mr-2 w-10/12 border-b-2 border-green-500">
                <button type="submit" value="Save" class="bg-green-500 w-2/12 
                text-white">Save</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                task: ""
            }
        },
        methods:{
            saveTask(){
                axios.post('/tasks', { todo: this.task,})
                    .then(response => { console.log(response)})
                    .catch(error => { console.log(error.response)});
                this.task = "";
                this.$router.push("/");
            }
        }
    }
</script>
