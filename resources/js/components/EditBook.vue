<template>
    <div>
        <h3>Edit Book</h3>
        <form @submit.prevent="updateBook">
            <div>
                <label>Name</label>
                <input type="text" v-model="book.name">
            </div>
            <div>
                <label>Author</label>
                <input type="text" v-model="book.author">
            </div>
            <button type="submit">Update Book</button>
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return {
            book:{}
        }
    },
    created(){
        this.axios
            .get(`http://localhost:8000/api/book/edit/${this.$route.params.id}`)
            .then(response => {
                console.log(response.data);
                this.book = response.data;
            });
    },
    methods: {
        updateBook(){
            this.axios
                .post(`http://localhost:8000/api/book/update/${this.$route.params.id}`, this.book)
                .then(response => {
                    this.$router.push({name:'home'});
                });
        }
    }
}
</script>