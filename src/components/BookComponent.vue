<script setup>
import FormBook from "./book/FormBook.vue";
import ListBook from "./book/ListBook.vue";
import { computed, reactive, ref } from "vue";
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
}

function reading(id) {
  booksCase.value.forEach((x) => {
    if (x.id == id) {
      x.isRead = !x.isRead;
    }
  });
  console.log(booksCase);
}
const total = computed(() => {
  return booksCase.value.length;
});
const lu = computed(() => {
  return booksCase.value.filter((x) => x.isRead).length;
});

function removing(id) {
  booksCase.value = booksCase.value.filter((x) => x.id != id);
}
</script>
<template>
  <FormBook @newBook="addBook" />
  <ListBook @remove="removing" @toRead="reading" :booksCase="booksCase" />
  <div>Total: {{ total }}</div>
  <div>Lu: {{ lu }}</div>
</template>

<style scoped></style>
