<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light w-100">
        <div class="container">
            <a class="navbar-brand" href="#">Base SPA</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item">
                        <nuxt-link class="nav-link" exact no-prefetch active-class="active" to="/">
                            Home
                        </nuxt-link>
                    </li>
                    <li class="nav-item">
                        <nuxt-link class="nav-link" no-prefetch active-class="active" to="/posts">
                            Posts
                        </nuxt-link>
                    </li>
                    <li class="nav-item" v-if="!hasToken">
                        <nuxt-link class="nav-link" no-prefetch active-class="active" to="/login">
                            Login
                        </nuxt-link>
                    </li>
                    <li class="nav-item" v-else>
                        <a class="nav-link" href="#" @click.prevent="logout">
                            Logout
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    computed: {
        hasToken() {
            return this.$store.getters.hasToken
        }
    },
    methods: {
        logout() {
            this.$store.dispatch('logout')
            this.$router.push('/login')
        }
    }
}
</script>