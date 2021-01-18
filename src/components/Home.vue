<template>
  <div class="contain">
    <h1 class="display-3 font-weight-light mb-4">
      Negocie e Consulte suas ações
    </h1>
    <v-sheet :elevation="6" class="pa-2" color="primary">
      <v-icon class="white--text mr-3">info</v-icon>
      <span class="headline white--text font-weight-light"
        >Você pode salvar & carregar os dados</span
      >
    </v-sheet>
    <v-sheet :elevation="6" class="pa-2" color="success">
      <v-icon class="white--text mr-3">info</v-icon>
      <span class="headline white--text font-weight-light"
        >Clique em 'Finalizar Dia' para iniciar um novo dia!</span
      >
    </v-sheet>
    <v-divider class="my-4"></v-divider>
    <p class="display-1"><strong >Seu Saldo:</strong> {{ funds }}</p>
    <v-divider class="my-4"></v-divider>
  </div>
</template>

<script>
export default {
  computed: {
    funds() {
      return this.$store.getters.funds
    }
  }

}
</script>

<style>

</style>
