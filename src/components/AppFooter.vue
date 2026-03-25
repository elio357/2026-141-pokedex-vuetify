<template>
  <!-- Pied de page global de l'application -->
  <v-footer>
    <!-- Conteneur centré sur toute la largeur -->
    <div class="px-4 text-center w-100">
      <!--
      slot = contenu personnalisable depuis le parent.
      Si rien n'est fourni, on affiche l'année courante + "Pokédex".
      -->
      <slot>{{ new Date().getFullYear() }} - Pokédex</slot>
    </div>
  </v-footer>
</template>
