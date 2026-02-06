<script setup>
import FormBook from "./book/FormBook.vue";
import ListBook from "./book/ListBook.vue";
import { computed, reactive, ref } from "vue";
const div = document.createElement("div");
function ID() {
  return Math.floor(Date.now() + Math.random() * 10);
}

let booksCase = ref([
  {
    id: ID(),
    title: "Clean Code",
    author: "Robert C. Martin",
    year: 2008,
    category: "Programmation",
    isRead: false,
  },
  {
    id: ID(),
    title: "Clean Code",
    author: "Robert C. Martin",
    year: 2008,
    category: "Programmation",
    isRead: false,
  },
]);

function addBook(nbook) {
  booksCase.value.push({
    id: ID(),
    title: nbook.title,
    author: nbook.author,
    year: nbook.year,
    category: nbook.category,
    isRead: false,
  });
  nbook.title = "";
  nbook.author = "";
  nbook.year = "";
  nbook.category = "";
}

function reading(id) {
  booksCase.value.forEach((x) => {
    if (x.id == id) {
      x.isRead = !x.isRead;
    }
  });
}
const total = computed(() => {
  return booksCase.value.length;
});
const lu = computed(() => {
  return booksCase.value.filter((x) => x.isRead).length;
});

function removing(id) {
  div.textContent = "";
  div.innerHTML = `<p>Supprimer ce livre?</p>
  <button class="yes" >Ok</button><button class="no" >Annuler</button>`;
  div.className = "modal";
  document.querySelector(".container").prepend(div);
  document.addEventListener("click", (e) => {
    if (e.target.classList.contains("yes")) {
      booksCase.value = booksCase.value.filter((x) => x.id != id);
      div.textContent = "";
      div.className = "";
    }
    if (e.target.classList.contains("no")) {
      div.textContent = "";
      div.className = "";
    }
  });
}
</script>
<template>
  <div class="container">
    <FormBook @newBook="addBook" />
    <div class="empty" v-if="total == 0">
      Your bookscase is empty... <br />
      Please add new books
    </div>
    <ListBook @remove="removing" @toRead="reading" :booksCase="booksCase" />
    <div v-if="total > 0">Total: {{ total }}</div>
    <div v-if="total > 0">Lu: {{ lu }}</div>
  </div>
</template>

<style scoped>
.empty {
  color: orange;
  text-align: center;
  font-weight: bold;
  margin-block: 6rem;
}

.container {
  color: #f8f8f8;
  width: 65%;
}
</style>

<style>
.modal {
  width: 16vw;
  height: 10vh;
  position: fixed;
  top: 50vh;
  right: 10vw;
  color: #0c0c0c;
  background-color: #f8f8f8f5;
  padding: 1%;
  text-align: center;
  border-radius: 7px;
  line-height: 30px;
}

.modal p {
  font-weight: bold;
  font-size: 1rem;
  color: orange;
}

.modal button {
  margin-inline: 10px;
  margin-top: 10px;
  color: rgb(0, 102, 255);
  background-color: transparent;
  border: 1px solid rgb(0, 102, 255);
  border-radius: 5px;
  padding-inline: 10px;
}
</style>
