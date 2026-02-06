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
  <header>
    <h1>
      Your Books
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640">
        <path
          d="M480 576L192 576C139 576 96 533 96 480L96 160C96 107 139 64 192 64L496 64C522.5 64 544 85.5 544 112L544 400C544 420.9 530.6 438.7 512 445.3L512 512C529.7 512 544 526.3 544 544C544 561.7 529.7 576 512 576L480 576zM192 448C174.3 448 160 462.3 160 480C160 497.7 174.3 512 192 512L448 512L448 448L192 448zM224 216C224 229.3 234.7 240 248 240L424 240C437.3 240 448 229.3 448 216C448 202.7 437.3 192 424 192L248 192C234.7 192 224 202.7 224 216zM248 288C234.7 288 224 298.7 224 312C224 325.3 234.7 336 248 336L424 336C437.3 336 448 325.3 448 312C448 298.7 437.3 288 424 288L248 288z"
        />
      </svg>
    </h1>
    <p>Bienvenue sur ton espace bibliothèque</p>
  </header>
  <form action="" @submit.prevent="toAdd(book)">
    <fieldset>
      <!-- <div> -->
      <input
        type="text"
        name="title"
        v-model="book.title"
        placeholder="Title"
        required
      />
      <input
        type="text"
        name="author"
        v-model="book.author"
        required
        placeholder="Author"
      />
      <!-- </div> -->
      <!-- <div> -->
      <input
        type="number"
        name="year"
        v-model="book.year"
        placeholder="Appear's Year"
        required
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
header {
  margin-bottom: 3rem;
}

h1 {
  text-shadow: 1px 1px 8px orange;
  font-weight: 700;
  font-size: 2.3rem;
}

h1 svg {
  height: 40px;
  /* padding-top: 30px; */
  fill: rgb(253, 166, 5);
  transform: translateY(20%);
}

p {
  font-size: 1.1rem;
}

fieldset {
  border: transparent;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  padding: 0;
  margin-block: 20px;
}
input {
  padding: 0.8rem;
  background-color: transparent;
  border: 1px rgb(102, 133, 153) solid;
  border-radius: 6px;
  color: aliceblue;
  outline: none;
}
button {
  width: 15rem;
  height: 40px;
  background-color: rgba(1, 46, 114, 0.979);
  border: 1px;
  color: white;
  cursor: pointer;
}


</style>
