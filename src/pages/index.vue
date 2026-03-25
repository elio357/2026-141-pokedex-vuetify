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
        <v-card>
          <!--
          Image du Pokémon responsive avec chargement progressif
            * :src lie dynamiquement le chemin de l'image
            * height="200" fixe la hauteur
            * cover remplit l'espace en gardant les proportions
          -->
          <v-img
            :src="getImageUrl(pokemon.img)"
            :alt="pokemon.name"
            height="200"
            cover
          />
          <!-- Nom du Pokémon -->
          <v-card-title>{{ pokemon.name }}</v-card-title>
          <!-- Niveau du Pokémon -->
          <v-card-subtitle>Niveau {{ pokemon.level }}</v-card-subtitle>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
// Import du helper pour construire les chemins d'images
import { getImageUrl } from '@/utils/imageUrl'

// Variable réactive contenant la liste des Pokémon (tableau vide au départ)
// ref() est auto-importé grâce à unplugin-auto-import
const pokemons = ref([])

// onMounted s'exécute une fois que le composant est affiché dans le navigateur
// C'est le bon endroit pour charger des données depuis une API
// Stockez la réponse JSON dans pokemons.value
onMounted(async () => {
  const response = await fetch('http://localhost:3535/pokemons')
  pokemons.value = await response.json()
  console.log('Pokémon chargés :', pokemons.value)
})
</script>
