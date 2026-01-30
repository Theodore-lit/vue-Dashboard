<script setup>
const emits = defineEmits(["toShow", "isActif"]);
function cliked(comp, statut) {
    emits("isActif", statut)
  emits("toShow", comp);
}
const props = defineProps({
  active: Boolean,
});
</script>

<template>
  <aside>
    <h3>Dashboard</h3>
    <ul>
      <li :class="props.active ? 'active' : ''" @click="cliked('Home')">
        Home
      </li>
      <li :class="props.active ? 'active' : ''" @click="cliked('Book')">Book</li>
      <li :class="props.active ? 'active' : ''" @click="cliked('Users')">Users</li>
      <li :class="props.active ? 'active' : ''" @click="cliked('FormUsers')">FormUsers</li>
      <li :class="props.active ? 'active' : ''" @click="cliked('Orders')">Orders</li>
      <li :class="props.active ? 'active' : ''" @click="cliked('Reports')">Reports</li>
      <li :class="props.active ? 'active' : ''" @click="cliked('Settings')">Settings</li>
    </ul>
  </aside>
</template>

<style scoped>
h3 {
  color: black;
  font-size: 2rem;
  font-weight: 500;
}
aside {
  width: 100%;
  padding: 1.2rem;
  height: 100vh;
}

li {
  height: 46px;
  margin-block: 20px;
  align-content: center;
  padding-inline-start: 0.5rem;
  background-color: white;
  cursor: pointer;
  font-size: 1.1rem;
  transition: all 0.2s ease-in-out;
}

li:hover {
  background-color: #ccccccdc;
  color: rgba(0, 0, 0, 0.788);
  border-radius: 4px;
}
.active {
  background-color: #ccccccdc;
  color: rgba(0, 0, 0, 0.788);
  border-radius: 4px;
}
</style>
