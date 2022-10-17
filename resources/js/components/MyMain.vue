<template>
    <div class="container">
        
        <h2 class="my-4">Posts</h2>
        
        <nav>
            <ul class="pagination ">
                <li class="page-item" :class="(curretPage == 1)?'disabled':''">
                    <a class="page-link" href="#" @click.prevent="apiFunction(curretPage - 1)">Previous</a>
                </li>
                <li class="page-item" :class="(curretPage == lastPage)?'disabled':''">
                    <a class="page-link" href="#" @click.prevent="apiFunction(curretPage + 1)">Next</a>
                </li>
            </ul>
        </nav>

        <div class="card col-12 my-4" v-for="(post, index) in posts" :key="index">
            <div class="card-body">
                <h5 class="card-title"><strong>Name: </strong>{{post.name}}</h5>
                <p class="card-text"><strong>Content: </strong>{{post.content}}</p>
                <p class="card-text"><strong>Category: </strong>{{post.category.name}}</p>
                <p v-for="(tag, index) in post.tags" :key="index" >Tag: {{tag.name}}</p>
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
                lastPage: null,
                curretPage: 1,
            }
        },
        methods:{
            apiFunction(page){
                axios.get('/api/posts', {
                    params:{
                        page: page,
                    }
                })
                .then(res => {
                    this.posts = res.data.results.data;

                    this.lastPage = res.data.results.last_page;
                    this.curretPage = res.data.results.current_page;

                    console.log(res.data.results.last_page);
                    console.log(res.data.results.current_page);
                })
            }
        },
        mounted(){
            this.apiFunction(1);
        },
    }
</script>

<style>

</style>