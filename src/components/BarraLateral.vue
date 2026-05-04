<template>
    <header>
        <h1 class="marca">
            <img class="logo" src="../assets/logo.png" alt="" srcset="">
        </h1>
        <p class="descricao">
            Organize seu foco com um ritmo mais leve e um visual mais acolhedor.
        </p>
        <button class="button" @click="alterarTema">
            {{ textoBotao }}
        </button>
    </header>

</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data() {
        return {
            modoEscuroAtivo: false
        }
    },
    computed:{
        textoBotao () {
            if(this.modoEscuroAtivo){
                return 'Desativar modo escuro';
            }
            return 'Ativar modo escuro';
        }
    },
    methods: {
        alterarTema() {
            this.modoEscuroAtivo = !this.modoEscuroAtivo;
            this.$emit('aoTemaAlterado', this.modoEscuroAtivo);
        }
    }
});

</script>

<style scoped>
header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 1.5rem;
    padding: 2rem;
    height: 100vh;
    width: 100%;
    background:
        radial-gradient(circle at top, rgba(255, 255, 255, 0.18), transparent 28%),
        linear-gradient(160deg, #7f5539 0%, #b5654d 52%, #ddb892 100%);
    color: #fff7ef;
    text-align: left;
    box-shadow: inset -1px 0 0 rgba(255, 255, 255, 0.08);
}

.marca {
    margin: 0;
}

.logo {
    max-width: 160px;
    filter: drop-shadow(0 12px 24px rgba(53, 28, 17, 0.35));
}

.descricao {
    max-width: 18rem;
    margin: 0;
    line-height: 1.6;
    color: rgba(255, 247, 239, 0.88);
}

.button {
    width: fit-content;
    border: none;
    border-radius: 999px;
    padding: 0.9rem 1.4rem;
    font-weight: 700;
    background: rgba(255, 248, 240, 0.92);
    color: #7f5539;
    box-shadow: 0 16px 30px rgba(76, 42, 28, 0.18);
    transition: transform 0.2s ease, box-shadow 0.2s ease, background-color 0.2s ease;
}

.button:hover {
    transform: translateY(-1px);
    box-shadow: 0 18px 34px rgba(76, 42, 28, 0.24);
    background: #ffffff;
}

@media only screen and (max-width: 768px) {
    header {
        align-items: center;
        padding: 2.5rem 1.5rem;
        height: auto;
        text-align: center;
    }

    .descricao {
        max-width: 100%;
    }
}
</style>
