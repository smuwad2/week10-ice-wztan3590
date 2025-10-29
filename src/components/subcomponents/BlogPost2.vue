<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props: {
            subject: String,
            entry: String,
            mood: String
        },
        computed: {
            imageSrc() {
            // Assumes mood matches image filename
            // e.g., "love" -> "public/assets/love.png"
            return `/assets/${this.mood}.png`
            }
        },
    }
</script>


<template>
    <div class="card" style="width: 14rem; margin-bottom: 1rem;">
        <img :src="imageSrc" class="card-img-top" alt="mood image">
        <div class="card-body">
        <h6 class="card-title">{{ subject }}</h6>
        <p class="card-text">{{ entry }}</p>
        </div>
        <slot></slot>
    </div>
</template>

