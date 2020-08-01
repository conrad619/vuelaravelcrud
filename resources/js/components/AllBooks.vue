<template>
    <div>
        <h3>All Books</h3>
        <table>
            <thead>
                <tr>
                    <td>ID</td>
                    <td>Name</td>
                    <td>Author</td>
                    <td>Created</td>
                    <td>Updated</td>
                    <td>Action</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="book in books" :key="book.id">
                    <td>{{ book.id }}</td>
                    <td>{{ book.name }}</td>
                    <td>{{ book.author }}</td>
                    <td>{{ book.created_at }}</td>
                    <td>{{ book.updated_at }}</td>
                    <td>
                        <div>  
                            <router-link :to="{name: 'edit', params: {id: book.id}}">
                                Edit
                            </router-link>
                            <button @click="deleteBook(book.id)">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    data(){
        return {
            books:[
            ],
        }
    },
    created(){
        this.axios
            .get('http://localhost:8000/api/books')
            .then(response => {
                console.log( response.data);
                this.books = response.data;
            });
    },
    methods: {
        deleteBook(id){
            this.axios
                .delete(`http://localhost:8000/api/book/delete/${id}`)
                .then(response => {
                    let i = this.books.map(item => item.id).indexOf(id);
                    this.books.splice(i, 1);
                });
        }
    }
}
</script>