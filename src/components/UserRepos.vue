<template>
    <Div>
        <ul v-if="everythingIsReady">
            <li  v-bind:key="item.id" v-for="item in arr" >{{item.name}}</li>
        </ul>
    </Div>    
</template>

<script>
export default {
    name: 'UserRepos',
    props: {
        userRepos: String,
    },
    created: async function(){
        await this.getRepos()
    }
    ,
    data: function(){
        return{
            arr: [],
            everythingIsReady: false,
            arrCount: 0,
        }
    },
    methods: {
        getRepos: async function() {
            this.arr = await fetch(this.userRepos)
                            .then(response => response.json())
            this.everythingIsReady = true
        }
       
    } 
}
</script>

<style>

</style>
