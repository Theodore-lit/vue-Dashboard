<script setup>
import { ref } from "vue";
import BookComponent from "./components/BookComponent.vue";
import FormUsersComponent from "./components/FormUsersComponent.vue";
import HomeComponent from "./components/HomeComponent.vue";
import OrdersComponent from "./components/OrdersComponent.vue";
import ReportsComponent from "./components/ReportsComponent.vue";
import SettingsComponent from "./components/SettingsComponent.vue";
import SideBarComponent from "./components/SideBarComponent.vue";
import UsersComponent from "./components/UsersComponent.vue";
function ID() {
  return Math.floor((Math.random * 10) + Date.now());
}
let Users = ref([{name: 'theo', stack: 'java', score: 60}]);
function addUser(us) {
  console.log(us);
  Users.value.push({
    id: ID(),
    name: us.name,
    stack: us.stack,
    score: us.score,
  });
}

let active = ref(false)
function statut(s){
  active.value = s
}

let c = ref("Home");
function showComponent(comp) {
  c.value = comp;
}
</script>

<template>
  <main>
    <SideBarComponent :active="active" @isActif="statut" @toShow="showComponent" class="sideBar" />
    <div class="board">
      <HomeComponent v-if="c == 'Home'" />
      <BookComponent v-if="c == 'Book'" />
      <UsersComponent :users="Users" v-if="c == 'Users'" />
      <FormUsersComponent @newUser="addUser" @showUser="showComponent" v-if="c == 'FormUsers'" />
      <OrdersComponent v-if="c == 'Orders'" />
      <ReportsComponent v-if="c == 'Reports'" />
      <SettingsComponent v-if="c == 'Settings'" />
    </div>
  </main>
</template>

<style scoped>
main {
  width: 100vw;
  display: flex;
  /* justify-content: center; */
  margin: auto;
}
.sideBar {
  width: 19vw;
  background-color: rgb(2, 105, 202);
}

.board {
  /* background-color: aliceblue; */
  width: 60vw;
  padding-inline: 5rem;
  padding-block: 1rem;
}
</style>
