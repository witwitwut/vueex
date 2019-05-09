<template>
    <article>
        <img :src="info.avatar_url" />
        <h3>{{info.login}}</h3>
        <p>{{info.blog}}</p>
        <UserRepos v-if="everythingIsReady" :userRepos="info.repos_url" />
    </article>

</template>

<script>
import UserRepos from "./UserRepos"
export default {
    name: 'GitUser',
    components: {
        UserRepos
    },
    props: {
        user: String,
    },

    created: async function(){
        await this.getUser()
    },
    
    data: function(){
        return{
            url: '',
            info: '',
            everythingIsReady: false,
            arrCount: UserRepos.data.arrCount
        }
    },
    methods: {
        getUser: async function() {
            this.url = 'https://api.github.com/users/' + this.user
            this.info = await fetch(this.url)
                            .then(response => response.json())
                            // .then(response => {

                            //     this.everythingIsReady = true
                            // })
            // console.log('log af info i GitUser', this.info);
            console.log(this.info.repos_url)
            this.everythingIsReady = true
        }
    }
}
</script>

<style>

</style>
