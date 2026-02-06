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
let active = ref("Home");
let c = ref("Home");
let Users = ref([{ name: "theo", stack: "java", score: 60 }]);
function addUser(us) {
  if (us.name && us.stack && us.score) {
    Users.value.push({
      name: us.name,
      stack: us.stack,
      score: us.score,
    });
    active.value = "Users";
  }
}

function statut(s) {
  active.value = s;
}

function showComponentByAdd(com,us){
  if (us.name && us.stack && us.score) {
    c.value = com
  }
}

function showComponent(comp) {
  c.value = comp;
}
</script>

<template>
  <main>
    <SideBarComponent
      :active="active"
      @isActif="statut"
      @toShow="showComponent"
      class="sideBar"
    />
    <div
      :class="
        c == 'Book'
          ? 'book'
          : c == 'Home'
            ? 'home'
            : c == 'FormUsers'
              ? 'userForm'
              : 'default'
      "
    >
      <div :class="c == 'Book' ? 'blur' : 'blurDefault'">
        <HomeComponent v-if="c == 'Home'" />
        <BookComponent v-if="c == 'Book'" />
        <UsersComponent :users="Users" v-if="c == 'Users'" />
        <FormUsersComponent
          @newUser="addUser"
          @showUser="showComponentByAdd"
          v-if="c == 'FormUsers'"
        />
        <OrdersComponent v-if="c == 'Orders'" />
        <ReportsComponent v-if="c == 'Reports'" />
        <SettingsComponent v-if="c == 'Settings'" />
      </div>
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
  width: 20vw;
  background-color: rgb(2, 105, 202);
}

.blur {
  backdrop-filter: blur(5px);
  height: 100%;
  width: 100%;
  padding-inline: 5rem;
  padding-block: 1rem;
}
.default {
  height: 100vh;
  width: 80vw;
  background-color: rgba(69, 115, 202, 0.582);
}
.blurDefault {
  backdrop-filter: blur(2px);
  height: 100%;
  width: 100%;
  padding-inline: 5rem;
  padding-block: 1rem;
}

.book {
  background: url(assets/Gemini_Generated_Image_4g01zs4g01zs4g01.png) no-repeat;
  background-position: center;
  background-size: cover;
  width: 80vw;
}

.home {
  background: url(assets/Capture\ d’écran\ 2026-01-31\ 133505.png) no-repeat;
  background-position: center;
  background-size: cover;
  width: 80vw;
}

.userForm {
  background: url(src/assets/Gemini_Generated_Image_1a6ax41a6ax41a6a.png)
    no-repeat;
  background-position: center;
  background-size: cover;
  width: 80vw;
}
</style>
