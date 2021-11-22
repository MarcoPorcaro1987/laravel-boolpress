<template>
    <ul>
        <li v-for="post in posts" :key="post.id">{{post.title}}</li>
    </ul>
</template>

<script>
    export default {
        name : "App",
        data(){
            return{
                posts : []
            }
        },
        mounted(){
            const axios = require('axios');

            // Make a request for a user with a given ID
            axios.get('/api/posts')
            .then((response)  => {
                // handle success
                this.posts = response.data.data;
            })
            .catch((error) =>{
                // handle error
                console.log(error);
            })
        }
    }
</script>