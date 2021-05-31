<template>
    <div class="container">
        <item v-for="acao in listaDeAcoes" :key="acao.symbol" :dadosDaAcao='acao' />
    </div>
</template>

<script>
import Item from './Item'

export default {
    name: 'container-acoes',
    props: {
        acaoParaEnviarRequest: String
    },
    data() {
        return {
            listaDeAcoes: []
        }
    },
    watch: {
        async acaoParaEnviarRequest(val) {
            if(val != '') {
                const res = await fetch('https://api.hgbrasil.com/finance/stock_price?format=json-cors&key=' + process.env.VUE_APP_API_KEY + val)
                const resJson = await res.json()

                let attrAcao = Object.keys(resJson.results)[0]
                if(!resJson.results[attrAcao].error) {
                    let acaoRepitidaFlag = false
                    this.listaDeAcoes.forEach((acao) => {
                        if(acao.symbol == resJson.results[attrAcao].symbol) { acaoRepitidaFlag = true }
                    })
                    if(acaoRepitidaFlag == false) this.listaDeAcoes.push(resJson.results[attrAcao])
                }
            }
        }
    },
    components: {
        Item
    },
}
</script>

<style scoped>
    .container {
        margin: auto;
        
        width: 639px;
        height: auto;

        display: flex;
        flex-flow: row wrap;
        justify-content: space-between;
    }
</style>