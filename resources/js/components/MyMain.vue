<template>
    <div class="container">
        <h2 class="my-4">Posts</h2>
        <div class="card col-12 my-4" v-for="(post, index) in posts" :key="index">
            <div class="card-body">
                <h5 class="card-title"><strong>Name: </strong>{{post.name}}</h5>
                <p class="card-text"><strong>Content: </strong>{{post.content}}</p>
                <p class="card-text"><strong>Category: </strong>{{post.category.name}}</p>
                <a href="#" class="btn btn-primary">More..</a>
            </div>
        </div>
    </div>
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