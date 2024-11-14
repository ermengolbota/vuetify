<template>
    <h1>Llistat</h1>
    <div class="cronograma">
        <div class="fitxa" v-for="fitxa in dades" :key="fitxa.Any">
            <div class="any">{{ fitxa.Any }}</div>
            <div class="teoric">{{ fitxa.Teòric }} </div>
            <div class="contribucio"> {{ fitxa.Contribució }}</div>
        </div>
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

.fitxa {
    color: black;
    background-color: white;
    border: 1px solid blue;
    width: 300px;
    margin: 10px;
    padding: 10px;
}

.fitxa .any {
    text-align: center;
    color: #444;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

.fitxa .teoric {
    color: #777;
    font-variant: small-caps;
    text-align: center;
    font-size: 1.1rem;
}

.fitxa .contribucio {
    color: #111;
    text-align: justify;
    font-size: .9rem;
}
</style>