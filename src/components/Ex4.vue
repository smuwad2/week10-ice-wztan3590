<script>
    import TaskTracker from './subcomponents/TaskTracker.vue'
    export default {
        data() {
            return {
                desc: '',
                deadline: '',
                taskList: []
            }
        },
        components: {
            TaskTracker
        },
        methods: {
            add() {
                this.taskList.push( { Desc: this.desc, Deadline: this.deadline } )
                this.desc = ''
                this.deadline = ''
            },
            // TODO: Add a new method, to delete a task completed
            removeTask(idx) {
                // Remove the task at index idx
                this.taskList.splice(idx, 1);
                // this.posts = this.posts.filter(post=>post.id!=id)
            }
        }
    }

</script>

<template>
    <div class="mb-3">
        <label for="desc" class="form-label">Task</label>
        <input type="text" class="form-control" id="desc" v-model='desc' placeholder="task">
    </div>
    <div class="mb-3">
        <label for="deadline" class="form-label">Deadline</label>
        <input type="date" class="form-control" id="deadline" v-model='deadline' placeholder="deadline">
    </div>

    <button type="button" @click="add" class="btn btn-primary">Add New Task</button>
    <hr>

    <div class="d-flex flex-wrap">
        <task-tracker 
            v-for="(task, idx) in taskList" 
            :key="idx" 
            :task="{ Name: task.desc, Deadline: task.deadline }"
            :idx="idx"
            @done="removeTask(idx)"
        />
    </div>
</template>

<style scoped>
.d-flex {
    display: flex;
    flex-wrap: wrap;
}  
</style>
