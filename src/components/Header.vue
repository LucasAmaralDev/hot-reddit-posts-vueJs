<template>
    <header>
        <div>
            <h2>Hot Reddit Posts</h2>
        </div>
        <nav v-show="links">
            <router-link to="/">Posts</router-link>
            <router-link to="/sugestoes">Deixe Uma Sugestão</router-link>
        </nav>
    </header>
</template>

<script>
export default {
    name: "Header",

    data(){
        return{
            links: false
        }
    }
}

</script>
<style>
header{
    display: flex;
    width: screen;
    background-color: #EF4444;
    color: #FfF;
    justify-content: center;
    align-items: center;
    padding: 10px 50px;
}

nav{
    display: flex;
    gap: 1.5rem;
}

a{
    color: #fff;
    text-decoration: none;
    font-weight: 700;
    transition: .5s;
}

a:hover{
    color: #fad4d4;
}

</style>