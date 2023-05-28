<template>
<nav class="navbar navbar-dark navbar-expand-sm bg-dark fixed-top">
    <div class="container">
    <a href="/" class="navbar-brand">
    <i class="fas fa-blog"></i> &nbsp;
    <img src="https://img.icons8.com/?size=512&id=8VtIvMYdaITD&format=png" width="50" height="50">
    </a>

    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarCollapse">
        <span class="navbar-toggler-icon"></span>
    </button>


    <div id="navbarCollapse" class="collapse navbar-collapse">
    <ul class="navbar-nav ml-auto">
        <li class="nav-item">
            <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
            <router-link class="nav-link active" aria-current="page" to="/users">Users</router-link>
        </li>
    </ul>
    </div>
    </div>
</nav>

</template>

<script>
    export default {
        name:'navbarApp'
    }
</script>

<style scoped>

</style>