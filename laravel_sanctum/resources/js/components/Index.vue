<template>
    <div>
        <router-link :to="{ name: 'get.index' }">Get</router-link>
        <router-link :to="{ name: 'user.login' }">Login</router-link>
        <router-link :to="{ name: 'user.personal' }">Personal</router-link>
        <router-link :to="{ name: 'user.registration' }">Registration</router-link>
        <a @click.prevent="logout" href="#">Logout</a>
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: "Index",

    methods: {
        logout() {
            axios.post('/logout')
                .then( res => {
                    localStorage.removeItem('x_xsrf_token')
                    this.$router.push({name: 'user.login'})
                })
        }
    }
}
</script>

<style scoped>

</style>
