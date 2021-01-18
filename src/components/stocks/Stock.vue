<template>
<v-flex class="pr-3 pb-3" xs12 md6 lg4>
  <v-card class="red lighten-1 white--text">
    <v-card-title class="headline">
      <strong>{{ stock.name }} <small>(Preço: {{ stock.price }})</small></strong>
    </v-card-title>
  </v-card>
  <v-card >
    <v-container fill-height>
      <v-text-field label="Quantidade" type="number" v-model.number="quantity" :error="insufficientFunds">
      </v-text-field>
        <v-btn @click="buyStock" :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(quantity)" class="red lighten-2 white--text">{{ insufficientFunds ? "Insuficiente" : 'Comprar' }}</v-btn>
    </v-container>
  </v-card>
</v-flex>
</template>

<script>
export default {
  props: ['stock'],
  data() {
    return {
      quantity: 0
    }
  },
  computed: {
    funds() {
      return this.$store.getters.funds
    },
    insufficientFunds() {
      return this.quantity * this.stock.price > this.funds
    }
  },
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      this.$store.dispatch('buyStock', order)
      this.quantity = 0
    }
  }

}
</script>

<style>

</style>