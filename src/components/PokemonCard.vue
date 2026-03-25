<template>
  <!-- Carte cliquable qui mène vers la page détail du Pokémon -->
  <v-card
    :to="`/pokemon/${pokemon.id}`"
    hover
  >
    <!-- Image du Pokémon (chargée depuis le dossier public/images) -->
    <v-img
      :src="getImageUrl(pokemon.img)"
      :alt="pokemon.name"
      height="200"
      cover
    />

    <!-- Nom et niveau affichés sur la carte -->
    <v-card-title>{{ pokemon.name }}</v-card-title>
    <v-card-subtitle>Niveau {{ pokemon.level }}</v-card-subtitle>
  </v-card>
</template>

<script setup>
import { getImageUrl } from '@/utils/imageUrl'

// Ce composant attend un objet pokemon en entrée
// (id, name, level, img, etc.)
defineProps({
  pokemon: {
    type: Object,
    required: true,
  },
})
</script>
