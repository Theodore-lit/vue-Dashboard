<script setup>
import Item from "./Item.vue";
const props = defineProps({
  booksCase: Array,
});

const emits = defineEmits(["remove", "toRead"]);
function remove(id) {
  emits("remove", id);
}
function read(id) {
  emits("toRead", id);
}
</script>

<template>
  <div class="booksListe">
    <Item
      v-for="(b, index) in booksCase"
      :key="b.id"
      :book="b"
      :index="index"
      @toRemove="remove"
      @toRead="read"
    />
  </div>
</template>

<style scoped>
.booksListe {
  margin-bottom: 3rem;
  margin-top: 6rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 25px;
}
</style>
