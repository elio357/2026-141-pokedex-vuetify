<template>
  <!-- Conteneur principal de la page -->
  <v-container>
    <!-- Titre de la page Favoris -->
    <!-- text-h3 = grande taille, text-center = centré, my-6 = marge verticale -->
    <h1 class="text-h3 text-center my-6">
      Mes favoris
    </h1>

    <!-- Message affiché quand aucun Pokémon n'est encore ajouté en favori -->
    <!-- type="info" = style informatif, variant="tonal" = style visuel plus doux -->
    <v-alert
      type="info"
      variant="tonal"
    >
      Vous n'avez pas encore de Pokémon favoris.
    </v-alert>
  </v-container>
</template>
