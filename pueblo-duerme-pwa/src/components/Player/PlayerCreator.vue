<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <h1 class="display-1 font-weight-bold">Pueblo Duerme</h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="7">
        <v-subheader>Selecciona el número de jugadores</v-subheader>
      </v-col>
      <v-col cols="4">
        <!-- v-autocomplete con el modelo numberPlayer, que sea un select desde 1 hasta 50 jugadores -->
        <v-autocomplete
          v-model="numberPlayer"
          :items="Array.from(Array(50).keys())"
          label="Jugadores"
          outlined></v-autocomplete>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

export default {
  name: 'PlayerCreator',
  data: () => ({
    numberPlayer: 5
  }),
};
</script>

