<script>
    // Import BlogPost component
    import blogPost from './subcomponents/BlogPost.vue'
	import axios from 'axios'
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        computed: {
            baseUrl() {
                if (window.location.hostname=='localhost')
                    return 'http://localhost:3000' 
                else {
                    const codespace_host = window.location.hostname.replace('5173', '3000')
                    return `https://${codespace_host}`;
                }
            }
        },
        created() { // created is a hook that executes as soon as Vue instance is created
            axios.get(`${this.baseUrl}/posts`)
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        },
        methods: {
            deletePost(id, idx) {
                axios.get(`${this.baseUrl}/deletePost?id=${id}`)
                .then(response => {
                    // Remove post from array after successful deletion
                    this.posts.splice(idx, 1)
                })
                .catch(error => {
                    alert("Error deleting post: " + error.message)
                })
            }
        }
    }
</script>

<template>
    <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <div>
    <blogPost
      v-for="(post, idx) in posts" 
      :key="idx"
      :subject="post.subject"
      :entry="post.entry"
      :mood="post.mood"
    >
    <button 
        class="btn btn-primary"
        @click="deletePost(post.id, idx)">
        Delete
    </button>
    </blogPost>
  </div>
</template>

