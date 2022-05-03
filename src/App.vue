<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <placar-display
      :total="total"
      :looses="looses"
      :victory="victory"
      @onRestart="onRestart"
      @onReset="onReset"
    ></placar-display>
    <div class="ports">
      <div v-for="n in qtdePorts" :key="n">
        <door-gift
          :number="n"
          @onOpen="onOpen"
          :hasGift="portGift === n"
          :isSelect="portSelect === n"
          :isOpen="openedPorts.includes(n)"
          @onSelect="onSelect"
        ></door-gift>
      </div>
    </div>
  </div>
</template>

<script>
import DoorGift from "./components/DoorGift.vue";
import PlacarDisplay from "./components/PlacarDisplay.vue";
export default {
  name: "App",
  components: { DoorGift, PlacarDisplay },
  data: function () {
    return {
      total: 0,
      victory: 0,
      looses: 0,
      qtdePorts: 3,
      openedPorts: [],
      portSelect: null,
      portGift: null,
    };
  },
  methods: {
    getPortGift: function () {
      let n = Math.ceil(Math.random() * this.qtdePorts);
      if (n <= 0 || n > this.qtdePorts) {
        n = 1;
      }
      return n;
    },
    onOpen: function (hasGift, number) {
      if (hasGift) {
        this.victory++;
        this.total++;
      }
      if (!this.openedPorts.length < this.qtdePorts && !hasGift) {
        this.looses++;
        this.total++;
      }
      this.openedPorts.push(number);
    },
    onSelect: function (number) {
      if (this.portGift === null) {
        this.portGift = this.getPortGift();
      }
      if (this.openedPorts.length < this.qtdePorts - 1) {
        this.portSelect = number;
      }
      if (this.openedPorts.length < this.qtdePorts - 2) {
        const range = Array.from(Array(this.qtdePorts).keys());
        const openPort = range.filter(
          (n) =>
            n !== number - 1 &&
            n !== this.portGift - 1 &&
            !this.openedPorts.includes(n + 1)
        );
        this.openedPorts.push(openPort[0] + 1);
      }
    },
    onReset: function () {
      this.total = 0;
      this.victory = 0;
      this.looses = 0;
      this.portSelect = null;
      this.openedPorts = [];
    },
    onRestart: function () {
      this.portSelect = null;
      this.openedPorts = [];
      let n = Math.ceil(Math.random() * this.qtdePorts);
      if (n <= 0 || n > this.qtdePorts) {
        n = 1;
      }
      this.portGift = this.getPortGift();
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat");
* {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html,
body {
  height: 100%;
}

body {
  color: #eee;
  background: #1a2980; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to bottom,
    #26d0ce,
    #1a2980
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to bottom,
    #26d0ce,
    #1a2980
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid #fff;
  background-color: #fff2;
  padding: 0.5rem;
  margin: 1.5rem 0 4rem 0;
}

.ports {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
.ports > div {
  margin: 0.5rem;
}
</style>
