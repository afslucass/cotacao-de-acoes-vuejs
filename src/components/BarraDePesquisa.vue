<template>
    <div class="barra-de-pesquisa">
        <input type="text" v-model='inputData' placeholder="Pesquise uma Acao na Bovespa">
    </div>
</template>

<script>
export default {
    name: 'barra-de-pesquisa',
    data() {
        return {
            inputData: ''
        }
    },
    watch: {
        inputData(val) {
            let oldValue = val
            
            setTimeout(() => {
                let newValue = this.inputData
                
                if(oldValue == newValue && newValue.replace(/\s/g, '').length) {
                    val = val.toLowerCase()
                    this.$emit('EnviarRequestDeAcao', val)
                }
            }, 2000);
        }
    },
}
</script>

<style scoped>
    .barra-de-pesquisa {
        margin-top: 200px;
        margin-bottom: 100px;
        
        display: flex;
        flex-flow: row nowrap;
        justify-content: center;
    }

    .barra-de-pesquisa > input {
        width: 400px;
        height: 30px;
        font-size: 20px;
        
        background-color: hsl(0, 0%, 96%);

        padding-left: 10px;
    }
</style>