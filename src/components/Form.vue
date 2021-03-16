<template>
    <template v-if="usage === 'create'">
        <div class="container">
            <label for="firstnameC">Prénom</label>
            <input v-model="newUser.firstName" type="text" class="form-control" id="firstnameC"
                   placeholder="Insérez votre prénom">
            <label for="lastnameC">Nom</label>
            <input v-model="newUser.lastName" type="text" class="form-control" id="lastnameC"
                   placeholder="Insérez votre nom">
            <label for="emailC">Email</label>
            <input v-model="newUser.email" type="email" class="form-control" id="emailC"
                   placeholder="Insérez votre email">
            <label for="birthdateC">Date de naissance</label>
            <input v-model="newUser.birthDate" type="date" class="form-control" id="birthdateC">
            <label for="avatarUrlC">Avatar URL</label>
            <input v-model="newUser.avatarUrl" type="url" class="form-control" id="avatarUrlC"
                   placeholder="Insérez l'url de votre avatar">
            <label for="genderC">Genre</label>
            <select class="form-select" id="genderC" v-model="newUser.gender">
                <option value="male">Homme</option>
                <option value="female">Femmme</option>
            </select>
            <button type="submit" class="btn btn-success" v-on:click="createUser">Créer</button>
        </div>
    </template>
    <template v-if="usage === 'edit'">
        <div class="container">
            <label for="firstname">Prénom</label>
            <input :value="user.firstName" type="text" class="form-control" id="firstname"
                   placeholder="Insérez votre prénom">
            <label for="lastname">Nom</label>
            <input :value="user.lastName" type="text" class="form-control" id="lastname"
                   placeholder="Insérez votre nom">
            <label for="email">Email</label>
            <input :value="user.email" type="email" class="form-control" id="email" placeholder="Insérez votre email">
            <label for="birthdate">Date de naissance</label>
            <input :value="user.birthDate" type="date" class="form-control" id="birthdate">
            <label for="avatarUrl">Avatar URL</label>
            <input :value="user.avatarUrl" type="url" class="form-control" id="avatarUrl"
                   placeholder="Insérez l'url de votre avatar">
            <label for="gender">Genre</label>
            <select class="form-select" id="gender" :value="user.gender">
                <option value="male">Homme</option>
                <option value="female">Femmme</option>
            </select>
            <button type="submit" class="btn btn-success">Editer</button>
        </div>
    </template>
</template>

<script>
import axios from "axios";

export default {
    name: "Form",
    data() {
        return {
            newUser: {}
        }
    },
    props: {
        user: Object,
        usage: String
    },
    methods: {
        createUser() {
            console.log(this.newUser);
            axios
                .post('http://localhost:6929/users', this.newUser)
                .then(response => console.log(response))
        },
        editUser() {

        },
        getUserById() {
            axios
                .get()
        }
    },
    created() {
        console.log(this.usage);
    }
}
</script>

<style scoped>
.container {
    text-align: start;
}

input, select {
    margin-bottom: 20px;
}
</style>
