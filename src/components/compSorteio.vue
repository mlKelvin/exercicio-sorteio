<template>
    <div>
        <label for="nomePessoa">Nome: </label>
        <input type="text" id="nomePessoa" v-model="nomePessoa" required>     <br/>
        <label for="generoPessoa">Gênero: </label>
        <input type="text" id="generoPessoa" v-model="generoPessoa" required> <br/>
        <input type="button" value="Adicionar" @click="adicionarPessoa"/>         <br/><br/>  

        <table>
        <tr>
            <th>Nome</th>
            <th>Gênero</th>
        </tr>
        <tr v-for='item in listaPessoas' :key="item.Nome">
            <td>
                {{item.Nome}}
            </td>
            <td>
                {{item.Genero}}
            </td>
        </tr>

    </table>
        
    </div>
</template>

<script>
export default {
    data(){
        return{
            nomePessoa: '',
            generoPessoa: '',
            listaPessoas: [],
        }
    },

    methods:{
        validar(){
        const achou = this.listaPessoas.some((p) => p != (p.nomePessoa == this.nomePessoa) && (p.generoPessoa == this.generoPessoa));
            if (achou) {
                alert("achou")
            return true
            }
        return false
        },
        adicionarPessoa(){
            if(!(this.listaPessoas.includes(this.nomePessoa, ))){
                if( (this.nomePessoa) && (this.generoPessoa) ){
                    this.listaPessoas.push ({Nome: this.nomePessoa, Genero: this.generoPessoa})
                }
            }
        }
    }
}
</script>

<style>
    table, th, td{
        border: 1px solid black;
    }
</style>