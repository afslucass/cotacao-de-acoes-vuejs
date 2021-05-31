<template>
    <div class="item">
        <div class="head-item">
            <div id="d1">{{ dadosDaAcao.symbol }}</div>
            <div id="d2">{{ dadosDaAcao.name }}</div>
            <div id="d3">{{ dadosDaAcao.market_cap }} Milhões R$</div>
        </div>
        <div :class="mudaCorSeEstaSubindoClass">{{ dadosDaAcao.price }} R$</div>
    </div>
</template>

<script>
export default {
    name: 'item',
    props: {
        dadosDaAcao: Object,
    },
    data() {
        return {
            mudaCorSeEstaSubindoClass: 'price-item'
        }
    },
    created() {
        console.log(this.dadosDaAcao)
        if(this.dadosDaAcao.change_percent > 0) {
            this.mudaCorSeEstaSubindoClass += ' pinta-verde'
        } else {
            this.mudaCorSeEstaSubindoClass += ' pinta-vermelho'
        }
    }

}
</script>

<style scoped>
    .item {
        height: 200px;
        width: 200px;

        background-color: hsl(0, 0%, 10%);

        border-radius: 10px;
        margin-bottom: 20px;
    }

    .head-item {
        margin-top: 30px;
        margin-left: 20px;
    }

    .head-item > #d1 {
        color: hsl(0, 0%, 80%);
        font-size: 36px;
    }

    .head-item > #d2, .head-item > #d3 {
        color: hsl(0, 0%, 60%);
        font-size: 13px;
    }

    .price-item {
        text-align: end;
        margin-right: 20px;
        font-size: 30px;
    }
    
    .pinta-vermelho {
        color: hsl(0, 67%, 30%);
    }

    .pinta-verde {
        color: hsl(120, 66%, 30%);
    }
</style>