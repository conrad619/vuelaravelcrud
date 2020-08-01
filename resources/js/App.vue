<template>
    <div class="container">
        <h1>Book App</h1>
        <nav>
            <router-link to="/">Home</router-link>
            <router-link to="/add">Add Book</router-link>
        </nav>
        <br>
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    
}
</script>