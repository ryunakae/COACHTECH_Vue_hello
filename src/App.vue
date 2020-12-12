<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header></Header>
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
    <p @click="userClick">{{clickSentence}}</p>
    <ul>
      <li v-for="(data,index) in list" :key="index">
        {{data.name}}は{{data.price}}円です <span v-if="data.price > 300">高い</span>
      </li>
    </ul>
    <label for="name">名前：</label><input type="text" id="name" v-model="name" />
    <label for="price">値段：</label><input type="text" id="price" v-model="price" />
    <button @click="addItem">追加</button><button @click="deleteItem">全削除</button>
    <ul id="itemPriceList">
      <li v-for="(item,index) in itemPriceList" :key="index">
        {{item.name}}は{{item.price}}円です
      </li>
    </ul>
    <input type="text" v-model="sendText" />
    <Child :receiveText="sendText" @getShiokuri="showShiokuri"></Child>
    <p v-for="(item,index) in shiokuriList" :key="index">
        {{item}}
    </p>
    <Footer></Footer>
    <SideMenu></SideMenu>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from "./components/Header";
import Footer from "./components/Footer";
import SideMenu from "./components/SideMenu";
import Child from "./components/Child";

export default {
  name: 'App',
  components: {
    // HelloWorld
    Header,
    Footer,
    SideMenu,
    Child
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
      clickSentence: "クリックする前のテキスト",
      list: [
        { name: "りんご", price: 200 },
        { name: "オレンジ", price: 100 },
        { name: "バナナ", price: 500 }
      ],
      name: "",
      price: 0,
      itemPriceList: [],
      sendText: "",
      shiokuriList: []
    };
  },
  computed: {
    woTax() {
      return this.apple + this.orange
    },
    wTax() {
      return this.woTax *1.1
    }
  },
  methods: {
    userClick() {
      if(this.clickSentence == "クリックする前のテキスト") {
        this.clickSentence = "クリックした後のテキスト"
      }
      else {
        this.clickSentence = "クリックする前のテキスト"
      }
    },
    addItem() {
      this.itemPriceList.push(
        {name: this.name, price: this.price}
      );
    },
    deleteItem() {
      this.itemPriceList.splice(
        {index: 1}
      );
    },
    showShiokuri(Shiokuri) {
      this.shiokuriList.push(Shiokuri);
    },
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
