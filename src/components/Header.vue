<template>
  <div id="main">
    <input type="text" v-model="user">
    <button v-on:click="userclick">住所自動入力</button>
    <p>Address :{{from}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return{
      from: "",
      user: ""

    }
  },
 methods:{
  async userclick(){
  const test = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.user}?&apiKey=1M9b5tZ0MrwrXMM5CWVODNawmTJfgAcs51O55cT`)
  console.log(test.data[0].allAddress);
  this.from = test.data[0].allAddress;
}
},
}
</script>