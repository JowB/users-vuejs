<template>
    <table id="tbl-users" class="table table-hover" v-if="usersFiltered.length">
        <thead>
        <tr>
            <th></th>
            <th>Nom</th>
            <th>Prénom</th>
            <th>Email</th>
            <th @click="changeSort">
                Age
                <i v-if="sortDirection" class="fa"
                   v-bind:class="[ sortDirection === 'asc' ? 'fa-sort-up' : 'fa-sort-down' ]"></i>
            </th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="user in usersFiltered" :key="user">
            <td>
                <router-link :to="{name : 'EditUser', params: {id: user.id, user: user} }">
                    <img :src="user.avatarUrl"/>
                </router-link>
            </td>
            <td class="td-text">
                <router-link :to="{name : 'EditUser', params: {id: user.id, user: user} }">
                    {{ user.lastName }}
                </router-link>
            </td>
            <td class="td-text">{{ user.firstName }}</td>
            <td class="td-text">{{ user.email }}</td>
            <td class="td-text">{{ user.age }}</td>
        </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: "TableUsers",
    props: {
        usersFiltered: Array,
        genderFilter: Array,
        search: String,
        sortDirection: String,
        changeSort: Function
    },
    watch: {
        changeSort() {
            this.$parent.changeSort()
        }
    }
}
</script>

<style scoped>
    table {
        width: 80%;
        margin: auto;
    }
    .td-text {
        padding-top: 75px !important;
    }
    img {
        width: 200px;
        padding-top: 0 !important;
    }
</style>
