<template>
    <div>
        <label for="nomePessoa">Nome: </label>
        <input type="text" id="nomePessoa" v-model="nomePessoa" required>     <br/>
        <label for="generoPessoa">Gênero: </label>
        <input type="text" id="generoPessoa" v-model="generoPessoa" required> <br/>
        <input type="button" value="Adicionar" @click="adicionarPessoa"/>         <br/>
        <input type="button" value="Sortear Aleatorio" @click="sortPessoaAleatoria"/> <br/>
        <label for="pessoaAleatoria"></label><br/><br/>
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
            <td>
                <a href="#" @click="excluir(p)">Excluir</a>
            </td>
        </tr>

    </table>
        
    </div>
    <footer>
        
    </footer>
</template>

<script>
export default {
    data(){
        return{
            nomePessoa: '',
            generoPessoa: '',
            listaPessoas: [],
            pessoaAleatoria: '',
        }
    },

    methods:{
        sortPessoaAleatoria(){
            this.pessoaAleatoria = this.listaPessoas.indexOf(2)
        },

        excluir(pessoa){
            this.listaPessoas.splice(this.listaPessoas.indexOf(pessoa), 1)
        },

        validar(){
        const achou = this.listaPessoas.some((p) => p != p.nomePessoa == this.nomePessoa);
        if (achou) {
            alert("achou")
            return true
        }
        return false
        },
        
        adicionarPessoa(){
            if( (this.nomePessoa) && (this.generoPessoa) && (this.validar) ){
                this.listaPessoas.push ({Nome: this.nomePessoa, Genero: this.generoPessoa})
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