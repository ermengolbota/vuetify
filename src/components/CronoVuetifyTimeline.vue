<template>
    <h1>Llistat</h1>
    <v-timeline class="cronograma" justify="auto" align="start">
        <v-timeline-item class="fitxa" dot-color="purple-lighten-2" v-for="fitxa in dades" :key="fitxa.Any">
            <template v-slot:opposite>
                <div class="any text-h4">{{ fitxa.Any }}</div>
            </template>
            <div class="teoric text-h5">{{ fitxa.Teòric }} </div>
            <div class="contribucio"> {{ fitxa.Contribució }}</div>
        </v-timeline-item>
    </v-timeline>
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
    width: 700px;
    margin: auto;
}
</style>