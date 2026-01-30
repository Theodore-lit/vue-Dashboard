<script setup>
const emits = defineEmits(['newUser', "showUser"])
const user = {
    name:'',
    stack:'',
    score: null,
}
function addNewUser(us){
    emits('newUser', us);
    emits('showUser', 'Users')
}
</script>
<template>
    <form @submit.prevent="addNewUser(user)">
        <input type="text" v-model="user.name" >
        <input type="text" v-model="user.stack" >
        <input type="text" v-model="user.score" >
        <button>Ajouter</button>
    </form>
</template>
<style scoped></style>