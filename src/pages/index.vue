<template>
  <h1>Índex</h1>
  <!-- Comenteu / descomenteu el component que volgueu veure-->
  <!-- El més senzill, tots els estils en la directuva style
  <CronoVueSimple />
  -->
  <!-- Utilitzant vuetify per fer v-card, no calen tants estils
   i aconseguim la mateixa aprença que amb vue+estils
    <CronoVuetifySimple />
    -->

  <!-- Utilitzant el component avançat v-timeline que ja està preparat
   per mostrar una línia de temps
   Molt poc css pròpi-->
  <CronoVuetifyTimeline />

</template>

<script setup>

import CronoVueSimple from '@/components/CronoVueSimple.vue';
import CronoVuetifySimple from '@/components/CronoVuetifySimple.vue';
import CronoVuetifyTimeline from '@/components/CronoVuetifyTimeline.vue';

</script>

<style>
h1 {
  text-align: center;
}
</style>