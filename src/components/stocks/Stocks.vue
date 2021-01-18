<template>
  <v-layout row wrap>
    <Stock v-for="stock in stocks" :key="stock.id" :stock="stock"></Stock>
  </v-layout>
</template>

<script>
import Stock from './Stock'

export default {
  components: { Stock },
  computed: {
    stocks() {
      return this.$store.getters.stocks
    }
  }

}
</script>

<style>

</style>