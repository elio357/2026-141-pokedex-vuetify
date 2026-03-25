<template>
  <!-- Conteneur principal — centre le contenu et limite la largeur -->
  <v-container>
    <!--
    Titre de la page
      * text-h3 : taille de titre niveau 3
      * text-center : centré horizontalement
      * my-6 : marge verticale (haut + bas) de 6 unités
    -->
    <h1 class="text-h3 text-center my-6">
      Pokédex
    </h1>

    <!--
    Grille responsive Vuetify (basée sur flexbox, 12 colonnes)
      * v-row = ligne
      * v-col = colonne, les breakpoints définissent combien de colonnes occuper
    -->
    <v-row>
      <!--
      v-for crée une colonne pour chaque Pokémon
        * :key est obligatoire — identifiant unique pour Vue
        * cols="12" : 1 carte/ligne sur mobile (12/12 = 100%)
        * sm="6" : 2 cartes/ligne sur tablette (6/12 = 50%)
        * md="4" : 3 cartes/ligne sur écran moyen (4/12 = 33%)
        * lg="3" : 4 cartes/ligne sur grand écran (3/12 = 25%)
      -->

      <!-- Colonne avec breakpoints responsive -->
      <v-col
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        cols="12"
        sm="6"
        md="4"
        lg="3"
      >
        <!-- La carte détaillée est déléguée au composant PokemonCard -->
        <PokemonCard :pokemon="pokemon" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import PokemonCard from '@/components/PokemonCard.vue'

// Variable réactive contenant la liste des Pokémon (tableau vide au départ)
// ref() est auto-importé grâce à unplugin-auto-import
const pokemons = ref([])

// onMounted s'exécute une fois que le composant est affiché dans le navigateur
// C'est le bon endroit pour charger des données depuis une API
// Stockez la réponse JSON dans pokemons.value
onMounted(async () => {
  const response = await fetch('http://localhost:3535/pokemons')
  pokemons.value = await response.json()
})
</script>
