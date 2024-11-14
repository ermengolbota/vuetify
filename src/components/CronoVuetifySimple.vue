<template>
    <h1>Llistat3</h1>
    <div class="cronograma">
        <v-card class="fitxa" v-for="fitxa in dades" :key="fitxa.Any" variant="outlined" max-width="300" hover>
            <template v-slot:title>
                <div class="any">{{ fitxa.Any }}</div>
            </template>
            <template v-slot:subtitle>
                <div class="teoric">{{ fitxa.Teòric }} </div>
            </template>
            <template v-slot:text>
                <div class="contribucio"> {{ fitxa.Contribució }}</div>
            </template>
        </v-card>
    </div>
    <h1>FI</h1>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const dades = ref([])


/*Funcio asincrona per fer el fetch
*/
async function carregarDades() {
    console.log("Carreguem")

    try {
        const resposta = await fetch('./historia.json')
        const tmp = await resposta.json()
        dades.value = tmp.IntroduccióHistòrica

    } catch (error) {
        console.error('Error carregant dades:', error)
    }
}

onMounted(() => {
    console.log("mounted")
    // Carreguem les dades a l inici
    //aqui no podem fer el await fetch per que la funcio no es async
    //per aixo tenim una funcio async per carregar-les
    carregarDades()
})

</script>

<style scoped>
.cronograma {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
</style>