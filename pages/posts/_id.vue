<template>
    <section>
        <h1>Post ({{post.title || 'Loading...'}})</h1>
        <h6>Created by: {{user.name || 'Loading...'}}</h6>

        <p>{{post.body}}</p>

        <h1>Comments</h1>
        <ul>
            <li v-for="comment of comments" :key="comment.id" class="comment-block">
                <p>{{comment.name}}<br />{{comment.body}}</p>
                <i>reply to <a href="#">{{comment.email}}</a></i>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    middleware: ['auth'],
    data: () => ({
        post: [],
        user: [],
        comments: []
    }),
    async mounted() {
        this.post = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts/' + this.$route.params.id)
        this.user = await this.$axios.$get('https://jsonplaceholder.typicode.com/users/' + this.post.userId)
        this.comments = await this.$axios.$get('https://jsonplaceholder.typicode.com/comments?postId=' + this.post.id)
    },
    validate({params}) {
        console.log('validate')
        return /^\d+$/.test(params.id)
    }
}
</script>

<style scoped>
.comment-block {
    border: solid 1px #000;
    margin: 8px 0;
    padding: 8px;
}
</style>