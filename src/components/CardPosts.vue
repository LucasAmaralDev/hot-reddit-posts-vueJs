<template>
    <section>
        <div class="container-post" v-for="post in posts" :key="post.id">
            <div class="container-title"> {{ post.titulo }}</div>
            
            <div class="container-autor-data">
                <p>Autor: {{ post.autor }}</p>
                <p>Data: {{ post.data_adicionado }}</p>
            </div>

            <div class="container-conteudo-post">
                <p v-for="paragrafo in post.conteudo.split('\n')">{{ paragrafo }}</p>
            </div>

            <div class="container-comentarios-link">
                <p>10 Comentários</p>

                <a :href="post.link_publicacao" target="_blank">
                    <button>Ver no Reddit</button>
                </a>
            </div>
            
        </div>
    </section>
</template>

<script>
export default {
    name: "CardPosts",

    data(){
        return{
            posts: null
        }
    },

    methods:{
        async getPosts(){
            const req = await fetch('https://api-reddit.devlucas.online/posts/findAll')
            const res = await req.json()
            this.posts = res
            console.log(this.posts)
        }
    },

    mounted(){
        this.getPosts()
    }
}
</script>

<style scoped>
    section {    
        width: 100%;
        max-width: 1024px;
        margin: 0 10px;
    }

    .container-post{
        width: 100%;
        max-width: 100%;
        overflow: auto;
        background-color: #F5F5F4;
        padding: 10px;
        border-radius: 3px;
        box-shadow: 0 2px 1px 1px rgba(0, 0, 0, 0.079);
        margin-bottom: 12px;
    }

    .container-title{
        text-align: center;
        color: #C24122;
        font-size: 1.3rem;
        padding-top: 10px;
    }

    .container-autor-data{
        display: flex;
        justify-content: space-between;
        padding: 0 18px;
    }

    .container-autor-data p{
        font-size: 0.8rem;
    }

    .container-conteudo-post{
        padding: 15px 15px;
    }

    .container-conteudo-post p{
        font-size: 1.2rem;
        text-align: justify;
    }

    .container-comentarios-link{
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 8px;
    }

    .container-comentarios-link button{
        font-size: 1.2rem;
        padding: 5px 15px;
        border-radius: 5px;
        background-color: rgb(192, 68, 182);
        color: #FFF;
        border: 2px solid #fdfdfd;
        transition: 0.5s;
    }

    .container-comentarios-link button:hover{
        background-color: rgb(233, 232, 233);
        color: rgb(192, 68, 182);
        border-color: rgb(179, 39, 167);;

    }
    
</style>