<script setup>
const props = defineProps({
  book: Object,
  index: Number,
});

const emits = defineEmits(["toRemove", "toRead"]);
function remove(id) {
  emits("toRemove", id);
}

function read(id) {
  emits("toRead", id);
}
</script>
<template>
  <span class="title">{{ props.book.title }}</span>
  <span>N°{{ props.index }}</span>
  <span class="author">{{ props.book.author }}</span>
  <span class="category">{{ props.book.category }}</span>
  <span class="year">{{ props.book.year }}</span>
  <span class="reading">
    <span class="readMsg">{{ props.book.isRead ? "Lu" : "À Lire" }}</span>
    <button class="readBtn" @click="read(props.book.id)">
      {{ props.book.isRead ? "Marquer non lu" : "Marquer lu" }}
    </button></span
  >
  <button @click="remove(props.book.id)">❌</button>
</template>
<style scoped>
.readMsg {
  height: 40px;
  width: 70px;
  background-color: black;
  color: white;
  text-align: center;
}

button {
    height: 30px;
    width: 100px;
}

.reading {
    display: flex;
    justify-content: center;
}
template {
    display: flex;
}
</style>
