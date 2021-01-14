<template>
    <div class="navbar">
        <h3 class="logo"><i class="fa fa-align-justify"></i> Banco</h3>
        <a  href="" @click.prevent="logout" class="logout"><i class="fa fa-sign-out-alt"></i> Sair</a>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    name: 'NavBarComponent',
    methods: {
        logout() {
            this.$router.push({name: 'login'});
        }
    }
})
</script>

<style lang="scss">

.navbar {
    .logo {
        color: #FFFFFF;
        font-weight: 200;
    }

    .logout {
        color: #FFFFFF;
        text-decoration: none;
    }
}

</style>