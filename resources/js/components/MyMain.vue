<template>

</template>

<script>
    export default {
        name: 'MyMain',
        data(){
            return{
                posts: [],
            }
        },
        methods:{
            apiFunction(){
                axios.get('/api/posts').then(res => {
                    this.posts = res.data.results;
                    console.log(res.data.results);
                })
            }
        },
        mounted(){
            this.apiFunction();
        },
    }
</script>

<style>

</style>