<template>

  <v-toolbar class="menu" app>
    <v-toolbar-title class="headline text-uppercase mr-4">
    <span>Stock</span>
    <span class="font-weight-light" >Trader</span>

    </v-toolbar-title>
    <v-toolbar-items>
      <v-btn flat to="/" class="menu-item"> <a>Início</a></v-btn>
      <v-btn flat to="/portfolio" class="menu-item"><a>Portfólio</a></v-btn>
      <v-btn flat to="/stocks" class="menu-item"><a>Ações</a></v-btn>
    </v-toolbar-items>

    <v-spacer></v-spacer>

    <v-toolbar-items class="segundo">
      <v-btn flat @click="endDay" class="white--text text--darken-2">Finalizar Dia</v-btn>
      <v-menu offset-y>
        <v-btn flat slot="activator" class="white--text text--darken-2">Salvar & Carregar</v-btn>
        <v-list>
          <v-list-tile @click="saveData">
            <v-list-tile-title>Salvar Dados</v-list-tile-title>
          </v-list-tile>
          <v-list-tile @click="loadDataLocal">
            <v-list-tile-title>Carregar Dados</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>
      <v-layout align-center>
        <span class="text-uppercase black--text text--darken-2">
          Saldo: {{ funds }}
        </span>
      </v-layout>
    </v-toolbar-items>
</v-toolbar>
</template>

<script>
import { mapActions } from 'vuex'

export default {
    computed: {
        funds() {
            return this.$store.getters.funds
        }
    },
    methods: {
        ...mapActions(['randomizeStocks', 'loadData']),
        endDay() {
            this.randomizeStocks()
        },
        saveData() {
            const { funds, stockPortfolio, stocks } = this.$store.getters
            this.$http.put('data.json', { funds, stockPortfolio, stocks })
        },
        loadDataLocal() {
            this.loadData()
        }
    }
}
</script>

<style>
body {
  display: flex;
  height: 100vh;
  padding: 0 5rem;
  box-sizing: border-box;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  background-image: #fff;
  font-family: "Open Sans", sans-serif;
}

.menu {
  
background: #EB3349;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #F45C43, #EB3349);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #F45C43, #EB3349); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

}
.menu a {
  color: rgb(255, 255, 255);
  text-decoration: none;
  font-weight: 600;
}
.menu a:focus, .menu a:focus-within {
  outline: none;
}
.menu > ol {
  display: flex;
  
}
.menu > ol > li {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (min-width: 45rem) {
  .menu > ol {
    justify-content: space-around;
  }
  .menu > ol:hover > li:first-child > a, .menu > ol:focus-within > li:first-child > a {
    opacity: 0.6;
  }
  .menu > ol > li {
    flex: 1 1 0;
  }
  .menu > ol > li:last-child:after {
    content: "";
    position: absolute;
    top: 0;
    width: 100%;
    bottom: 0;
    margin-right: -50%;
    background: rgba(0, 0, 0, 0.1);
    border-radius: 0.5rem;
    z-index: 0;
    transition: 350ms cubic-bezier(1, 0.49, 0.09, 1.29) all;
    pointer-events: none;
  }
  .menu > ol > li:first-child:nth-last-child(1) ~ li:last-child:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(2) ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:after {
    right: 650%;
  }
  .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:after {
    right: 750%;
  }
  .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:after {
    right: 850%;
  }
  .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:after {
    right: 950%;
  }
  .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:after {
    right: 1050%;
  }
  .menu > ol > li:first-child:nth-last-child(2):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(2):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(2):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(2):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(2) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(2):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(2):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(2):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(2) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(2) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(2) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(3):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(3):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.6666666667);
  }
  .menu > ol > li:first-child:nth-last-child(3):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(3):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.6666666667);
  }
  .menu > ol > li:first-child:nth-last-child(3):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(3):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(3):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(3):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(3):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.3333333333);
  }
  .menu > ol > li:first-child:nth-last-child(3):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(3):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(3) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.3333333333);
  }
  .menu > ol > li:first-child:nth-last-child(3):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(3):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(3):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(3) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.75);
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.75);
  }
  .menu > ol > li:first-child:nth-last-child(4):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(4):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(4):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(4):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(4):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(4):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.25);
  }
  .menu > ol > li:first-child:nth-last-child(4):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(4):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(4) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.25);
  }
  .menu > ol > li:first-child:nth-last-child(4):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(4):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(4):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(4) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.8);
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.8);
  }
  .menu > ol > li:first-child:nth-last-child(5):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.6);
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.6);
  }
  .menu > ol > li:first-child:nth-last-child(5):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.4);
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.4);
  }
  .menu > ol > li:first-child:nth-last-child(5):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.2);
  }
  .menu > ol > li:first-child:nth-last-child(5):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(5) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.2);
  }
  .menu > ol > li:first-child:nth-last-child(5):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(5) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.8333333333);
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.8333333333);
  }
  .menu > ol > li:first-child:nth-last-child(6):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.6666666667);
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.6666666667);
  }
  .menu > ol > li:first-child:nth-last-child(6):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(6):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.3333333333);
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.3333333333);
  }
  .menu > ol > li:first-child:nth-last-child(6):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.1666666667);
  }
  .menu > ol > li:first-child:nth-last-child(6):nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6):nth-child(5):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(6) ~ li:nth-child(5):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.1666666667);
  }
  .menu > ol > li:first-child:nth-last-child(6):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(6) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 650%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.8571428571);
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.8571428571);
  }
  .menu > ol > li:first-child:nth-last-child(7):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.7142857143);
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.7142857143);
  }
  .menu > ol > li:first-child:nth-last-child(7):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5714285714);
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5714285714);
  }
  .menu > ol > li:first-child:nth-last-child(7):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.4285714286);
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.4285714286);
  }
  .menu > ol > li:first-child:nth-last-child(7):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.2857142857);
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(5):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(5):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.2857142857);
  }
  .menu > ol > li:first-child:nth-last-child(7):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.1428571429);
  }
  .menu > ol > li:first-child:nth-last-child(7):nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7):nth-child(6):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(7) ~ li:nth-child(6):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.1428571429);
  }
  .menu > ol > li:first-child:nth-last-child(7):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(7) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 750%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.875);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.875);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 650%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.75);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.75);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.625);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.625);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.375);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(5):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(5):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.375);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.25);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(6):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(6):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.25);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.125);
  }
  .menu > ol > li:first-child:nth-last-child(8):nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8):nth-child(7):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(8) ~ li:nth-child(7):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.125);
  }
  .menu > ol > li:first-child:nth-last-child(8):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(8) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 850%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.8888888889);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.8888888889);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 750%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.7777777778);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.7777777778);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 650%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.6666666667);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.6666666667);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5555555556);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5555555556);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.4444444444);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(5):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(5):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.4444444444);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.3333333333);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(6):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(6):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.3333333333);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.2222222222);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(7):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(7):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.2222222222);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(8):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(8):hover > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus > ol a, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):hover > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus > ol a, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.1111111111);
  }
  .menu > ol > li:first-child:nth-last-child(9):nth-child(8):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9):nth-child(8):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(9) ~ li:nth-child(8):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.1111111111);
  }
  .menu > ol > li:first-child:nth-last-child(9):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(9) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 950%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.9);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.9);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 850%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.8);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.8);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 750%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.7);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.7);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 650%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.6);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.6);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus-within ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(5):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(5):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.4);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(6):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(6):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.4);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.3);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(7):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(7):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.3);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(8):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(8):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.2);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(8):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(8):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(8):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.2);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(9):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(9):hover > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus > ol a, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):hover > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus > ol a, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.1);
  }
  .menu > ol > li:first-child:nth-last-child(10):nth-child(9):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10):nth-child(9):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(10) ~ li:nth-child(9):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.1);
  }
  .menu > ol > li:first-child:nth-last-child(10):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(10) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus-within ~ li:last-child:after {
    right: 1050%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.9090909091);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(1):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(1):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.9090909091);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus-within ~ li:last-child:after {
    right: 950%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.8181818182);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(2):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(2):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.8181818182);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus-within ~ li:last-child:after {
    right: 850%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.7272727273);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(3):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(3):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.7272727273);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus-within ~ li:last-child:after {
    right: 750%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.6363636364);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(4):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(4):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.6363636364);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus-within ~ li:last-child:after {
    right: 650%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.5454545455);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(5):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(5):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.5454545455);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus-within ~ li:last-child:after {
    right: 550%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.4545454545);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(6):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(6):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.4545454545);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus-within ~ li:last-child:after {
    right: 450%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.3636363636);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(7):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(7):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.3636363636);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(8):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus-within ~ li:last-child:after {
    right: 350%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(8):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.2727272727);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(8):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(8):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(8):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.2727272727);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(9):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus-within ~ li:last-child:after {
    right: 250%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(9):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.1818181818);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(9):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(9):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(9):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.1818181818);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(10):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus-within ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):hover ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus ~ li:last-child:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus-within ~ li:last-child:after {
    right: 150%;
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(10):hover > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus > ol a, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus-within > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):hover > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus > ol a, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus-within > ol a {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0), inset 0 0 0 3rem rgba(237, 110, 160, 0.0909090909);
  }
  .menu > ol > li:first-child:nth-last-child(11):nth-child(10):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11):nth-child(10):focus-within > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):hover > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):hover > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):hover > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus > ol a:focus-within, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus-within > ol a:hover, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus-within > ol a:focus, .menu > ol > li:first-child:nth-last-child(11) ~ li:nth-child(10):focus-within > ol a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1), inset 0 0 0 3rem rgba(237, 110, 160, 0.0909090909);
  }
  .menu > ol > li:first-child:nth-last-child(11):last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11):last-child:focus-within:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:hover:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus:after, .menu > ol > li:first-child:nth-last-child(11) ~ li:last-child:focus-within:after {
    right: 50%;
  }
  .menu > ol > li:first-child > a {
    opacity: 1;
  }
  .menu > ol > li > a {
    padding: 2rem 0;
    font-size: 1.6vw;
    position: relative;
    width: 100%;
    text-align: center;
    z-index: 1;
    opacity: 0.7;
    transition: 250ms ease all;
  }
  .menu > ol > li > ol {
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    visibility: hidden;
  }
  .menu > ol > li > ol > li {
    margin-top: 0.5rem;
    transition: 250ms cubic-bezier(0.42, 0.83, 0.49, 1.35) transform;
    transform: scale(0);
  }
  .menu > ol > li > ol > li > a {
    display: block;
    text-align: center;
    border-radius: 0.2rem;
    padding: 1rem 0.5rem;
    font-size: 1.4vw;
    background: #ec8c69;
    color: rgba(255, 255, 255, 0.6);
    transition: 250ms ease all;
  }
  .menu > ol > li > ol > li > a:hover, .menu > ol > li > ol > li > a:focus, .menu > ol > li > ol > li > a:focus-within {
    box-shadow: inset 0 0 0 3rem rgba(0, 0, 0, 0.1);
    color: white;
  }
  .menu > ol > li:hover > a, .menu > ol > li:focus > a, .menu > ol > li:focus-within > a {
    opacity: 1 !important;
  }
  .menu > ol > li:hover > ol, .menu > ol > li:focus > ol, .menu > ol > li:focus-within > ol {
    visibility: visible;
  }
  .menu > ol > li:hover > ol > li, .menu > ol > li:focus > ol > li, .menu > ol > li:focus-within > ol > li {
    transform: scale(1);
  }
  .menu > ol > li:hover > ol > li:first-child, .menu > ol > li:focus > ol > li:first-child, .menu > ol > li:focus-within > ol > li:first-child {
    transition-delay: 150ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(1), .menu > ol > li:focus > ol > li:nth-child(1), .menu > ol > li:focus-within > ol > li:nth-child(1) {
    transition-delay: 150ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(2), .menu > ol > li:focus > ol > li:nth-child(2), .menu > ol > li:focus-within > ol > li:nth-child(2) {
    transition-delay: 300ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(3), .menu > ol > li:focus > ol > li:nth-child(3), .menu > ol > li:focus-within > ol > li:nth-child(3) {
    transition-delay: 450ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(4), .menu > ol > li:focus > ol > li:nth-child(4), .menu > ol > li:focus-within > ol > li:nth-child(4) {
    transition-delay: 600ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(5), .menu > ol > li:focus > ol > li:nth-child(5), .menu > ol > li:focus-within > ol > li:nth-child(5) {
    transition-delay: 750ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(6), .menu > ol > li:focus > ol > li:nth-child(6), .menu > ol > li:focus-within > ol > li:nth-child(6) {
    transition-delay: 900ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(7), .menu > ol > li:focus > ol > li:nth-child(7), .menu > ol > li:focus-within > ol > li:nth-child(7) {
    transition-delay: 1050ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(8), .menu > ol > li:focus > ol > li:nth-child(8), .menu > ol > li:focus-within > ol > li:nth-child(8) {
    transition-delay: 1200ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(9), .menu > ol > li:focus > ol > li:nth-child(9), .menu > ol > li:focus-within > ol > li:nth-child(9) {
    transition-delay: 1350ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(10), .menu > ol > li:focus > ol > li:nth-child(10), .menu > ol > li:focus-within > ol > li:nth-child(10) {
    transition-delay: 1500ms;
  }
  .menu > ol > li:hover > ol > li:nth-child(11), .menu > ol > li:focus > ol > li:nth-child(11), .menu > ol > li:focus-within > ol > li:nth-child(11) {
    transition-delay: 1650ms;
  }
}
@media (max-width: 45rem) {
  .menu {
    background-image: linear-gradient(to bottom, #ed6ea0 0%, #ec8c69 100%);
  }
  .menu a {
    font-size: 1.4rem;
    padding: 1rem 0.5rem;
  }
  .menu > ol {
    flex-direction: column;
  }
  .menu > ol > li {
    flex-direction: column;
    align-items: stretch;
    text-align: center;
  }
  .menu > ol > li > a:nth-last-child(2) {
    position: relative;
  }
  .menu > ol > li > a:nth-last-child(2):after {
    content: "";
    position: absolute;
    top: 50%;
    margin-top: -0.25rem;
    right: 1.5rem;
    border-top: 0.5rem solid #fff;
    border-left: 0.3rem solid transparent;
    border-right: 0.3rem solid transparent;
    transition: 250ms ease all;
  }
  .menu > ol > li:focus-within:nth-last-child(2):after, .menu > ol > li:focus:nth-last-child(2):after,
.menu > ol > li > a:hover:nth-last-child(2):after,
.menu > ol > li > a:focus-within:nth-last-child(2):after,
.menu > ol > li > a:focus:nth-last-child(2):after {
    transform: rotate(180deg);
  }
  .menu > ol > li:focus-within + ol, .menu > ol > li:focus + ol,
.menu > ol > li > a:hover + ol,
.menu > ol > li > a:focus-within + ol,
.menu > ol > li > a:focus + ol {
    max-height: 12rem;
  }
  .menu > ol > li > ol {
    background: rgba(0, 0, 0, 0.1);
    box-shadow: inset 0.1rem 0.1rem 0.5rem rgba(0, 0, 0, 0.15);
    overflow: hidden;
    max-height: 0;
    transition: 250ms ease all;
  }
  .menu > ol > li > ol > li a {
    display: block;
    font-size: 1.2rem;
  }
}
</style>