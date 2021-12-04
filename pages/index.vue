<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="8">
      <v-card>
        <v-card-title class="headline">
          Bienvenido a LuxApp Noticias
        </v-card-title>
        <v-card-text>
          <p>Esta es una página web diseñada para brindarte las noticias más recientes con una interfaz novedosa.</p>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="accent"
            nuxt
            to="/news"
          >
            Ver Noticias
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
}
</script>
