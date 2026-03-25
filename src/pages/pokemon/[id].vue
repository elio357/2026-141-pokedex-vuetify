<template>
  <!-- Conteneur principal de la page détail -->
  <v-container>
    <!-- Bouton de retour vers la page précédente -->
    <v-btn
      variant="text"
      prepend-icon="mdi-arrow-left"
      class="mb-4"
      @click="$router.back()"
    >
      Retour
    </v-btn>

    <!-- Message affiché si aucun Pokémon ne correspond à l'id de l'URL -->
    <v-alert
      v-if="!pokemon"
      type="error"
      variant="tonal"
    >
      Pokémon non trouvé.
    </v-alert>

    <!-- Sinon, on affiche la fiche détaillée du Pokémon -->
    <v-card
      v-else
      max-width="800"
      class="mx-auto"
    >
      <!-- Image principale du Pokémon -->
      <v-img
        :src="getImageUrl(pokemon.img)"
        :alt="pokemon.name"
        height="300"
        cover
      />

      <!-- Nom du Pokémon -->
      <v-card-title class="text-h4">
        {{ pokemon.name }}
      </v-card-title>

      <!-- Niveau du Pokémon -->
      <v-card-subtitle>
        Niveau {{ pokemon.level }}
      </v-card-subtitle>

      <!-- Description affichée uniquement si elle existe -->
      <v-card-text>
        <p
          v-if="pokemon.description"
          class="text-body-1 mb-4"
        >
          {{ pokemon.description }}
        </p>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup>
import { getImageUrl } from '@/utils/imageUrl'

// Donne accès aux paramètres de l'URL (ici: route.params.id)
const route = useRoute()

// Liste locale des Pokémon chargée depuis l'API
const pokemons = ref([])

// Recherche le Pokémon correspondant à l'id présent dans l'URL
const pokemon = computed(() => {
  return pokemons.value.find(p => p.id === route.params.id)
})

// Chargement des données au montage de la page
onMounted(async () => {
  const response = await fetch('http://localhost:3535/pokemons')
  pokemons.value = await response.json()
})
</script>
