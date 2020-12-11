<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <h1>Hello world</h1>
    <table>
      <tr><th>名前</th><th>値段</th><th>個数</th></tr>
      <tr>
        <td>{{pencil.name}}</td>
        <td>{{pencil.price}}</td>
        <td>{{pencil.quantity}}</td>
      </tr>
      <tr>
        <td>{{eraser.name}}</td>
        <td>{{eraser.price}}</td>
        <td>{{eraser.quantity}}</td>
      </tr>
      <tr>
        <td>{{note.name}}</td>
        <td>{{note.price}}</td>
        <td>{{note.quantity}}</td>
      </tr>
    </table>
    <input type="text" :value="n">
    <p>合計金額：{{ woTax }}円（税抜）</p>
     <p>合計金額：{{ wTax }}円（税抜）</p>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      pencil: {
        name: "鉛筆",
        price: 100,
        quantity: 0
      },
      eraser: {
        name: "消しゴム",
        price: 100,
        quantity: 0
      },
      note: {
        name: "ノート",
        price: 100,
        quantity: 0
      },
      n: "hello",
      apple: 200,
      orange: 100,
    };
  },
  computed: {
    woTax() {
      return this.apple + this.orange
    },
    wTax() {
      return this.woTax *1.1
    }
  }
};
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
