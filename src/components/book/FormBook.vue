<script setup>
import { reactive } from "vue";
const book = reactive({
  title: "",
  author: "",
  year: null,
  category: "",
  isRead: null,
});

const emits = defineEmits(["newBook"]);
function toAdd(b) {
  emits("newBook", b);
}
</script>
<template>
  <h1>Your Books</h1>
  <p>Bienvenue sur ton espace bibliothèque</p>
  <form action="" @submit.prevent="toAdd(book)">
    <fieldset>
      <!-- <div> -->
        <input
          type="text"
          name="title"
          v-model="book.title"
          placeholder="Title"
        />
        <input
          type="text"
          name="author"
          v-model="book.author"
          placeholder="Author"
        />
      <!-- </div> -->
      <!-- <div> -->
        <input
          type="text"
          name="year"
          v-model="book.year"
          placeholder="Appear's Year"
        />
        <input
          type="text"
          name="category"
          v-model="book.category"
          placeholder="Book's ategory"
        />
      <!-- </div> -->
    </fieldset>
    <button>Ajouter</button>
  </form>
</template>
<style scoped>
fieldset {
  border: transparent;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  padding: 0;
  margin-block: 20px;
}
input {
  padding: .8rem;
  background-color: transparent;
  border: 1px gray solid;
  border-radius: 6px;
}
button {
  width: 15rem;
  height: 40px;
  background-color: rgb(2, 79, 194);
  border: 1px;
  color: white;
  font-weight: lighter;
  cursor: pointer; 
}
</style>
