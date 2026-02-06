<script setup>
const emits = defineEmits(["toShow", "isActif"]);
function cliked(comp) {
  emits("isActif", comp);
  emits("toShow", comp);
}
const props = defineProps({
  active: {
    type: String,
    default: false,
  },
});
</script>

<template>
  <aside>
    <h3>Dashboard</h3>
    <ul>
      <li
        :class="props.active == 'Home' ? 'active' : ''"
        @click="cliked('Home')"
      >
        Home
      </li>
      <li
        :class="props.active == 'Book' ? 'active' : ''"
        @click="cliked('Book')"
      >
        Book
      </li>
      <li
        :class="props.active == 'Users' ? 'active' : ''"
        @click="cliked('Users')"
      >
        Users
      </li>
      <li
        :class="props.active == 'FormUsers' ? 'active' : ''"
        @click="cliked('FormUsers')"
      >
        FormUsers
      </li>
      <li
        :class="props.active == 'Orders' ? 'active' : ''"
        @click="cliked('Orders')"
      >
        Orders
      </li>
      <li
        :class="props.active == 'Reports' ? 'active' : ''"
        @click="cliked('Reports')"
      >
        Reports
      </li>
      <li
        :class="props.active == 'Settings' ? 'active' : ''"
        @click="cliked('Settings')"
      >
        Settings
      </li>
    </ul>
  </aside>
</template>

<style scoped>
h3 {
  color: orange;
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
  color: black;
}

li:hover {
  background-color: gainsboro;
  color: rgba(0, 0, 0, 0.788);
  border-radius: 4px;
}
.active {
  background-color: #fffcfc8f ;
  color: rgba(0, 0, 0, 0.788);
  border-radius: 4px;
}
</style>
