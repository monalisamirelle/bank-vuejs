<template>
    <div>
        <div class="my-card">
            <div class="content top">
                <h3><i class="fa fa-money-bill-alt"></i> Conta Corrente</h3>
            </div>

            <div class="content footer">
                <h4>Saldo: <b v-if="conta != null">R$ {{conta.saldo}}</b></h4><i v-if="conta != null">A transação será para o(a) títular <br><b>{{conta.titular}}</b></i>
                <br>
            </div>
            <hr>
            <div class="form-saque-deposito">
                <div class="form">
                    <form>
                        <div class="form-group">
                            <label for="valor">Valor da Transação</label>
                            <input v-model="valor" type="text" class="form-control" id="valor" aria-describedby="valor" placeholder="">
                        </div>
                    </form>
                </div>
                <div class="row margin-button">
                    <div class="col-md-12">
                        <button style="margin-bottom: 10px;" class="btn btn-block btn-danger" data-toggle="modal" @click="sacar()">Saque</button>
                    </div>
                    <div class="col-md-12 ">
                        <button class="btn btn-block btn-success" @click="depositar()">Deposito</button>
                    </div>
                </div>
            </div>
        </div>


        <div class="lists">
            <div class="top">
                <strong>Contas</strong>
                <hr>
            </div>

            <div class="content">
                <table class="table table-striped">
                <thead>
                    <tr>
                    <th scope="col">Agencia</th>
                    <th scope="col">Conta</th>
                    <th scope="col">Títular</th>
                    <th scope="col">Saldo</th>
                    <th scope="col">#</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="conta in contas" :key="conta.id">
                        <td>{{conta.agencia}}</td>
                        <td>{{conta.numero_conta}}</td>
                        <td>{{conta.titular}}</td>
                        <td>{{conta.saldo}}</td>
                        <td><button @click="carregar(conta)" class="btn btn-block btn-primary"><i class="fa fa-hand-pointer" ></i> Selecionar Conta</button></td>
                    </tr>
                </tbody>
                </table>
            </div>

        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue';
import axios from 'axios';
Vue.prototype.$http = axios;

export default Vue.extend({
    name: 'ListComponent',
    mounted() {
        this.conta = null;
        this.valor = null;
        this.getContas();
    },
    data() {
        return {
            conta: null,
            valor: 0,
            contas: []
        }
    },
    methods: {
        carregar(c) {
            this.conta = c;
        },
        depositar() {
            let val = Number(this.valor.replace(/[^0-9.-]+/g,""));
            this.$http.put('http://localhost:8000/api/depositar/'+this.conta.id, {valor: val}).then((response) => {
                if (response.status == 200) {
                    this.getContas();
                }
            });
        },
        sacar() {
            this.$http.put('http://localhost:8000/api/sacar/'+this.conta.id, {valor: this.valor}).then((response) => {
                if (response.status == 200) {
                    this.getContas();
                }
            });
        },
        getContas() {
            this.$http.get('http://localhost:8000/api/').then((response) => {
                if (response.status == 200) {
                    this.contas = response.data.contas;
                    this.contas.map(value => {
                        let saldo = parseFloat(value.saldo.toString().replace('.','')).toFixed(2);
                        value.saldo = parseFloat(saldo).toLocaleString('pt-br',{style: 'currency', currency: 'BRL'});  
                    });
                }
            })
        }
    }
})
</script>

<style lang="scss" scoped>

.form-saque-deposito {
    width: 200px;
}

.lists {
    width: 100%;
    padding: 15px;
    border: 10x solid #ccc;
    background-color: #fff;
}

@import '@/assets/scss/_main';

.my-card {

    .buttons {
        button {
            margin: 10px;
        }
    }

    display: flex;
    flex-direction:  column;
    background-color: $purble;
    padding: 15px;
    border-radius: 7px;
    color: #fff;

    .content {
        display: flex;
        justify-content: space-between;
    }
}

</style>