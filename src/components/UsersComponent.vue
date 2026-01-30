<script setup>
const props = defineProps({
    users: Array,
})

</script>
<template>
    <div class="userContainer">
        <h1>Liste des utilisateurs</h1>
        <div class="user" v-for="us in props.users" :key="us.id">
            <h4>{{ us.name }}</h4>
            <p class="stack" >{{ us.stack }}</p>
            <p class="score">{{ us.score }}/100</p>
        </div>
    </div>
</template>
<style scoped></style>