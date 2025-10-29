<script>
    // TODO: Complete the code
    export default { 
        data() {
            return {
                
            }
        },
        // Hint: insert properties task (Object) and idx (Number)
        props: {
            task: Object,
            idx: Number
        },
        emits: ['removeTask']
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
    <div class="card" style="width: 18rem; margin: 0.5rem;">
        <div class="card-body">
            <h5 class="card-title">Deadline: {{ task.deadline }}</h5>
            <hr></hr>
            <p>{{ task.desc }}</p>
            <button class="btn btn-primary mt-3" @click="$emit('removeTask',idx)">Done</button>
        </div>
  </div>
</template>


