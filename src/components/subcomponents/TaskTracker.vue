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
        methods: {
            markDone() {
                this.$emit('Done', this.idx);
            }
        }

</script>

<template>
    <!-- TODO: add your template code here --> 
    <div class="card" style="width: 18rem; margin: 0.5rem;">
        <div class="card-body">
            <p>{{ task.desc }}</p>
            <h5 class="card-title">Deadline: {{ task.deadline }}</h5>
            <button class="btn btn-primary mt-3" @click="markDone">Done</button>
        </div>
  </div>
</template>


