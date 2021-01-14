<template>
    <div class="main">
        <div class="login">
            <div class="content-login">
                <header>
                    <h1>Login</h1>
                </header>

                <div class="form">
                    <form>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input type="email" class="form-control" id="email" aria-describedby="emailHelp" placeholder="">
                        </div>
                        <div class="form-group">
                            <label for="senha">Senha</label>
                            <input type="senha" class="form-control" id="senha" placeholder="">
                        </div>
                        <button type="submit" class="btn btn-primary" @click.prevent="login">Entrar</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>


<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    name: 'LoginComponent',

    data(){
        return {

        }
    },

    methods: {
        login() {
            this.$router.push({name: 'home'});
        }
    }
})
</script>

<style lang="scss" src="./style.scss" scoped />