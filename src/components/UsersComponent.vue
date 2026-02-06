<script setup>
const props = defineProps({
  users: Array,
});
</script>
<template>
  <div class="userContainer">
    <h1>Liste des utilisateurs</h1>
    <div class="userContaint">
      <div class="user" v-for="us in props.users">
        <h4>{{ us.name }}</h4>
        <p class="stack">{{ us.stack }}</p>
        <p class="score">{{ us.score }}/100</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.userContainer {
  background-color: white;
  width: 50%;
  margin: auto;
  padding-inline: 2%;
  padding-block: 10px;
  box-shadow: -1px 0px 9px orange;
  margin-top: 3rem;
  border-radius: 6px;
}

.userContaint {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.user {
  position: relative;
  height: 56px;
  padding-inline-start: 2%;
  align-items: center;
  background-color: rgba(214, 205, 194, 0.521);
  border-radius: 2px;
}

h4 {
  color: #111111;
  font-weight: 600;
}

.score {
  position: absolute;
  right: 3%;
  top: 25%;
  font-weight: bold;
  color: #3f3f3f;
}

.stack {
  color: rgba(84, 84, 84, 0.65);
}
</style>
