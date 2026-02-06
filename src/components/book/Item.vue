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
  <div class="book">
    <span>N°{{ props.index +1 }}</span>
    <span class="title">{{ props.book.title }}</span>
    <span class="category">{{ props.book.category }}</span>
    <span class="author">{{ props.book.author }}</span>
    <span class="year">{{ props.book.year }}</span>
    <span class="reading">
      <span class="readBadge"> <svg v-if="props.book.isRead == true" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640"><path d="M320 205.3L320 514.6L320.5 514.4C375.1 491.7 433.7 480 492.8 480L512 480L512 160L492.8 160C450.6 160 408.7 168.4 369.7 184.6C352.9 191.6 336.3 198.5 320 205.3zM294.9 125.5L320 136L345.1 125.5C391.9 106 442.1 96 492.8 96L528 96C554.5 96 576 117.5 576 144L576 496C576 522.5 554.5 544 528 544L492.8 544C442.1 544 391.9 554 345.1 573.5L332.3 578.8C324.4 582.1 315.6 582.1 307.7 578.8L294.9 573.5C248.1 554 197.9 544 147.2 544L112 544C85.5 544 64 522.5 64 496L64 144C64 117.5 85.5 96 112 96L147.2 96C197.9 96 248.1 106 294.9 125.5z"/></svg></span>  <span class="readBadge"><svg  v-if="!props.book.isRead" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640"><path d="M192 576L512 576C529.7 576 544 561.7 544 544C544 526.3 529.7 512 512 512L512 445.3C530.6 438.7 544 420.9 544 400L544 112C544 85.5 522.5 64 496 64L448 64L448 233.4C448 245.9 437.9 256 425.4 256C419.4 256 413.6 253.6 409.4 249.4L368 208L326.6 249.4C322.4 253.6 316.6 256 310.6 256C298.1 256 288 245.9 288 233.4L288 64L192 64C139 64 96 107 96 160L96 480C96 533 139 576 192 576zM160 480C160 462.3 174.3 448 192 448L448 448L448 512L192 512C174.3 512 160 497.7 160 480z"/></svg></span>

      <button class="readBtn" @click="read(props.book.id)">
        {{ props.book.isRead ? "Marquer non lu" : "Marquer lu" }}
      </button></span
    >
    <span class="remover" @click="remove(props.book.id)"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640"><path d="M232.7 69.9C237.1 56.8 249.3 48 263.1 48L377 48C390.8 48 403 56.8 407.4 69.9L416 96L512 96C529.7 96 544 110.3 544 128C544 145.7 529.7 160 512 160L128 160C110.3 160 96 145.7 96 128C96 110.3 110.3 96 128 96L224 96L232.7 69.9zM128 208L512 208L512 512C512 547.3 483.3 576 448 576L192 576C156.7 576 128 547.3 128 512L128 208zM216 272C202.7 272 192 282.7 192 296L192 488C192 501.3 202.7 512 216 512C229.3 512 240 501.3 240 488L240 296C240 282.7 229.3 272 216 272zM320 272C306.7 272 296 282.7 296 296L296 488C296 501.3 306.7 512 320 512C333.3 512 344 501.3 344 488L344 296C344 282.7 333.3 272 320 272zM424 272C410.7 272 400 282.7 400 296L400 488C400 501.3 410.7 512 424 512C437.3 512 448 501.3 448 488L448 296C448 282.7 437.3 272 424 272z"/></svg></span>
  </div>
</template>
<style scoped>
.title,.category, .author {
  width: 150px;
  justify-content: center;
  overflow: hidden;
}

.readBtn {
  /* background-color: rgb(0, 153, 255); */
  color: rgb(0, 153, 255);
  border: transparent;
  border-radius: 30px;
  height: 29px;
  /* color: white; */
  background-color: rgb(255, 255, 255);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-style: italic;
  transform: translateY(1px);
  cursor: pointer;
}

.reading {
  transform: translateX(20px);
  display: flex;
  justify-content: center;
  gap: 5px;
}
.book {
  border: 1.9px solid rgb(0, 153, 255);
  display: flex;
  height: 70px;
  align-items: center;
  padding-inline: 1rem;
  gap: 20px;
  position: relative;
  border-radius: 4px;
}

.remover {
  position: absolute;
  right: 2%;
  cursor: pointer;
}

.remover svg {
  fill: rgb(158, 3, 3);
  height: 23px;
}

.readBadge svg {
  height: 30px;
  fill: rgba(255, 166, 0, 0.993);
  stroke: rgba(4, 39, 63, 0.568);
  stroke-width: 10px;
}
</style>
