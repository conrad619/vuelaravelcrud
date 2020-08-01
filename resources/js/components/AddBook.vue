<template>
    <div>
        <h3>Add Book</h3>   
        <form @submit.prevent="addBook">
            <div>  
                <label>Name</label>
                <input type="text" v-model="book.name">
            </div>
            <div>  
                <label>Author</label>
                <input type="text" v-model="book.author">
            </div>
            <button type="submit">Add Book</button>
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
    methods: {
        addBook(){

            this.axios
                .post('http://localhost:8000/api/book/add',this.book)
                .then(response => (
                    this.$router.push({name:'home'})
                ))
                .catch(error => console.log(error));
        }
    }
}
</script>