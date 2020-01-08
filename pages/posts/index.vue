<template>
    <section>
        <h1>Posts</h1> 

        <ul>
            <li v-for="post of posts" :key="post.id">
                <a href="#" @click.prevent="openPost(post)">
                    {{post.title}}
                </a>
                <p>{{post.body}}</p>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    middleware: ['auth'],
    data: () => ({
        posts: []
    }),
    async mounted() {
        this.posts = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts')
    },
    methods: {
        openPost(post) {
            this.$router.push('/posts/' + post.id)
        }
    }
}
</script>