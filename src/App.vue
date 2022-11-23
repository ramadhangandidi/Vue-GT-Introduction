<template>
  <div id="app">
    <!-- Penggunaan v-once & v-text & v-on:click -->
    <div>
      <h1 v-once>Nama menggunakan v-once = {{ nama }}</h1>
      <h1 v-text="'Nama non v-once = '+ nama"></h1>
      <button v-on:click="gantiNama()">Ganti Nama Diatas</button>
    </div>

    <!-- Penggunaan v-bind -->
    <div>
      <img alt="Vue logo" v-bind:src="gambarMotor">
    </div>

    <!-- Penggunaan v-html -->
    <div v-html="page"></div>

    <!-- Penggunaan v-on:keyup.space -->
    <div>
      <label for="" style="margin-right: 10px">Input</label>
      <input v-on:keyup.space="gantiNama()" type="text" style="margin-top: 50px;">
    </div>

    <!-- Pengunaan v-model -->
    <div>
      <label for="" style="margin-right: 10px">V MODEL</label>
      <input v-model="nama" type="text" style="margin-top: 50px; margin-bottom: 100px;">
    </div>

    <!-- Penggunaan v-for -->
    <div>
      <h1>Hasil Dari v-for</h1>
      <h2 v-for="item in anggota" v-bind:key="item">Nama anggota : {{ item }}</h2>
    </div>

    <!-- Penggunaan v-if -->
    <div style="margin-top: 100px">
      <h1>Pengunaan v-if</h1>
      <h2 v-if="nama == 'Kodehive'">Kodehive Academy</h2>
      <h2 v-else-if="nama == 'Adhan'">Ramadhan Toxic Academy</h2>
      <h2 v-else>Bubar Bubar</h2>
    </div>

    <!-- Penggunaan v-show -->
    <div style="margin-top: 100px">
      <h1>Hasil dari v-show</h1>
      <h2 v-show="nama == 'Kodehive'">Kodehive Academy</h2>
      <h2 v-show="nama == 'Adhan'">Ramadhan Toxic Academy</h2>
      <h2 v-show="nama == 'nanang'">Bubar Bubar</h2>
    </div>

    <!-- Penggunaan computed property & methods -->
    <div style="margin-top: 100px">
      <h2>{{ totalBelanja }}</h2>
      <button v-on:click="gantiQuantity()">Ganti Qty</button>
    </div>


  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data: function(){
    return{
      nama : "Kodehive",
      anggota : ["Bayu", "Eka", "Rangga", "Adhan"],
      quantity : 5,
      page : `<h1 v-once>Halo, nama saya Bayu</h1>`,
      bold : "font-weight-bold",
      gambarMotor : "data:image/jpeg;base64,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"
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
    },
    gantiNama2 : function(){
      this.nama = "Adhan"
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
