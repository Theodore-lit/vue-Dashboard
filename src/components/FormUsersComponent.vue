<script setup>
const emits = defineEmits(["newUser", "showUser"]);
const user = {
  name: "",
  stack: "",
  score: null,
};
function addNewUser(us) {
  emits("newUser", us);
  emits("showUser", "Users", us);
}
</script>
<template>
  <div class="formContainer">
    <header>
      <h1>Formulaire d'ajout</h1>
      <p>Ajoutez de nouveaux devs à votre bibliothèque</p>
    </header>
    <form @submit.prevent="addNewUser(user)">
      <fieldset>
        <input type="text" v-model="user.name" placeholder="Name" />
        <input type="text" v-model="user.stack" placeholder="Stack"/>
        <input type="number" v-model="user.score" placeholder="Score/100" />
        <button>Ajouter</button>
      </fieldset>
    </form>
  </div>
</template>
<style scoped>
h1 {
  font-weight: bold;
  font-size: 2.3rem;
}

p {
  font-weight: 500;
  font-size: 1rem;
  text-shadow: 1px 1px 8px orange;
}
header {
  color: white;
  text-align: center;
}
fieldset {
  border: none;
  display: flex;
  flex-direction: column;
  gap: 30px;
}
.formContainer {
  width: 40%;
  margin: auto;
  padding-block: 5rem;
}

form {
  margin-top: 3rem;
}

input {
  padding: 0.8rem;
  background-color: transparent;
  border: 1px #44d6ea solid;
  border-radius: 6px;
  color: aliceblue;
  outline: none;
}

button {
  height: 40px;
  width: 100%;
  margin: auto;
  background-color: #44d6ea;
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: all .2s ease-in-out;
}

button:hover {
    transform: translateY(-3px);
}
</style>
