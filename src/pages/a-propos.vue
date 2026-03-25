<template>
  <!-- Conteneur principal de la page -->
  <v-container>
    <!-- Titre de la page -->
    <!-- text-h3 = grand titre, text-center = centré, my-6 = marge verticale -->
    <h1 class="text-h3 text-center my-6">
      À propos
    </h1>

    <!-- Carte qui encadre le contenu de présentation -->
    <!-- max-width limite la largeur, mx-auto centre la carte -->
    <v-card
      max-width="800"
      class="mx-auto"
    >
      <!-- Zone de texte interne de la carte -->
      <v-card-text>
        <!-- Premier paragraphe: définition du Pokédex -->
        <p class="text-body-1 mb-4">
          Le <strong>Pokédex</strong> est une encyclopédie électronique portable conçue pour
          cataloguer et fournir des informations sur les différentes espèces de Pokémon.
        </p>
        <!-- Deuxième paragraphe: contexte du projet et technologies -->
        <p class="text-body-1 mb-4">
          Cette application web a été développée dans le cadre du cours <strong>C141</strong>
          à l'ESIG, en utilisant <strong>Vue.js 3</strong>, <strong>Vuetify 3</strong>,
          <strong>Pinia</strong> et <strong>Axios</strong>.
        </p>
      </v-card-text>
    </v-card>
  </v-container>
</template>
