<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Halo, nama saya {{ nama }}</h1>
    <h2>Kalau saya {{ anggota[0] + " " + anggota[1] }}</h2>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <button 
      v-on:click="gantiNama()">
      Ganti Nama</button>

    <h2>{{ totalBelanja }}</h2>
    <button v-on:click="gantiQuantity()">Ganti Qty</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data: function(){
    return{
      nama : "Kodehive",
      anggota : ["Bayu", "Eka", "Rangga"],
      quantity : 5
    }
  },
  methods: {
    gantiNama : function(){
      if(this.nama == "Kodehive"){
        this.nama = "Adhan"
      }else{
        this.nama = "Kodehive"
      }
    },
    gantiQuantity : function(){
      this.quantity++
    }
  },
  computed: {
    totalBelanja : function(){
      return this.quantity * 10000
    }
  },

  components: {
    // HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
