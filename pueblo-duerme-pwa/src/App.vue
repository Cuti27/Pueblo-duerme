<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >

      <div class="d-flex align-center">
        <v-btn
          text
          href="/"
        >
          <h1 class="display-1 font-weight-bold">
            Pueblo Duerme
          </h1>
        </v-btn>
      </div>



    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
