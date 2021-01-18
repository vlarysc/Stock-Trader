<template>
<v-flex class="pr-3 pb-3" xs12 md6 lg4>
  <v-card class="green lighten-1 white--text">
    <v-card-title class="headline">
      <strong>{{ stock.name }} <small>(Preço: {{ stock.price }} | Qtede: {{ stock.quantity }})</small></strong>
    </v-card-title>
  </v-card>
  <v-card >
    <v-container fill-height>
      <v-text-field label="Quantidade" type="number" v-model.number="quantity" :error="insufficientQuantity">
      </v-text-field>
        <v-btn @click="sellStock" :disabled="insufficientQuantity || quantity <= 0 || !Number.isInteger(quantity)" class="pink lighten-2 white--text">{{ insufficientQuantity ? 'Insuficiente' : 'Vender' }}</v-btn>
    </v-container>
  </v-card>
</v-flex>
</template>

<script>
import { mapActions } from 'vuex'

export default {
    props: ['stock'],
    data() {
        return {
            quantity: 0
        }
    },
    computed: {
        insufficientQuantity() {
            return this.quantity > this.stock.quantity
        }
    },
    methods: {
        ...mapActions({ sellStockAction: 'sellStock' }),
        sellStock() {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            this.sellStockAction(order)
            // this.$store.dispatch('sellStock', order)
            this.quantity = 0
        }
    }
}
</script>

<style>

</style>