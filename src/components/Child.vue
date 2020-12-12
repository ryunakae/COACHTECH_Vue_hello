<template>
  <div id="child">
    <button @click="addItem">子に送る</button>
    <ul>
      <li v-for="(item,index) in list" :key="index">
        {{item.text}}
      </li>
    </ul>
    <input type="text" v-model="Shiokuri" />
    <button @click="sendShiokuri">仕送り</button>
  </div>
</template>

<script>
export default {
  props: ["receiveText"],
  data() {
    return {
      list: [],
      Shiokuri: ""
    }
  },
  methods: {
    addItem() {
      this.list.push({
        text: this.receiveText
      });
    },
    sendShiokuri() {
      this.$emit("getShiokuri", this.Shiokuri);
      this.Shiokuri = "";
    }
  }
};
</script>

<style scoped>
</style>