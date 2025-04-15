<template>
    <div class="body-wrapper">
      <h2 class="title">Book List</h2>
  <div class="mycontent">
    <table class="table table-striped text-center table-bordered">
    
      <thead>
        <tr>
          <th>ISBN</th>
          <th>Title</th>
          <th>Author</th>
          <th>Published Year</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in Books" :key="item.isbn">
          <td>{{ item.isbn }}</td>
          <td>{{ item.title }}</td>
          <td>{{ item.author }}</td>
          <td>{{ item.publishedYear }}</td>
        </tr>
      </tbody>
    </table>
  </div>

  <button class="btn btn-primary add-book" @click="showModal.value = true">Add Book</button>

  <div v-if="showModal.value" class="modal-overlay" @click="closeModal">
    <div class="modal-content" @click.stop>
      <div class="modal-header">
        <h5>Add New Book</h5>
        <button type="button" class="close-btn" @click="closeModal">&times;</button>
      </div>
      <div class="modal-body">
        <form @submit.prevent="addBook">
          <div class="form-group">
            <label>Title:</label>
            <input type="text" class="form-control" v-model="newBook.title" required />
          </div>
          <div class="form-group">
            <label>Author:</label>
            <input type="text" class="form-control" v-model="newBook.author" required />
          </div>
          <div class="form-group">
            <label>Published Year:</label>
            <input type="number" class="form-control" v-model="newBook.publishedYear" required />
          </div>
          <div class="form-group">
            <label>ISBN:</label>
            <input type="text" class="form-control" v-model="newBook.isbn" required />
          </div>
          <button type="submit" class="btn btn-primary" >Add</button>
        </form>
      </div>
    </div>
  </div>
</div>

</template>

<script setup>
import { reactive } from 'vue'

const Books = reactive([
  {
    title: "The Great Gatsby",
    author: "F. Scott Fitzgerald",
    publishedYear: 1925,
    genre: "Fiction",
    isbn: "9780743273565"
  },
  {
    title: "1984",
    author: "George Orwell",
    publishedYear: 1949,
    genre: "Dystopian",
    isbn: "9780451524935"
  },
  {
    title: "To Kill a Mockingbird",
    author: "Harper Lee",
    publishedYear: 1960,
    genre: "Classic",
    isbn: "9780061120084"
  }
])

const newBook = reactive({
  title: "",
  author: "",
  publishedYear: "",
  isbn: ""
})

const showModal = reactive({
  value: false
})

function addBook() {
  Books.push({ ...newBook })
  newBook.title = ""
  newBook.author = ""
  newBook.publishedYear = ""
  newBook.isbn = ""
  showModal.value = false
}

function closeModal() {
  showModal.value = false
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  animation: fadeIn 0.3s ease-in-out;
}

.modal-content {
  background-color: #fff;
  padding: 20px;
  width: 400px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  position: relative;
  animation: slideIn 0.3s ease-in-out;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 20px;
  background: none;
  border: none;
  cursor: pointer;
  color: #333;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.modal-body {
  margin-top: 20px;
}

.form-group {
  margin-bottom: 15px;
}

.form-group label {
  display: block;
  margin-bottom: 5px;
}

.form-control {
  width: 100%;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.mycontent {
  display: flex;
  justify-content: center;
  align-self: start;
  margin-top: 20px;
}

.book-container {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

.title {
  color: crimson;
  margin-bottom: 1rem;
}

table {
  margin: 0 auto;
  width: 100%;
  max-width: 700px;
}

.add-book {
  margin-top: 20px;
  background-color: blueviolet;
  border: none;
}

.body-wrapper {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
  padding: 20px;
}
</style>

