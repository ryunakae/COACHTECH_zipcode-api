<template>
  <div class="home">
    <input type="text" v-model="zipcode" maxlength="8" />
    <button @click="getAddressByZip">Zip Code</button>
    <!-- <button @click="outputAddress()">output</button> -->
    <p>Address：{{ allAddress }}</p>
    <p>〒{{ zip }}</p>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: 'Home',
  data() {
    return {
      zip: "",
      allAddress: "",
      item: "",
    };
  },
  methods: {
    async getAddressByZip() {
      this.zip = this.zipcode
      let item = await axios.get(
      `https://apis.postcode-jp.com/api/v4/postcodes/${this.zip}?apiKey=ZCxePaJWxCZcvFWy8cuRrA01Sca4rCOZ8HsGePl`
      );
      this.allAddress = item.data.allAddress;
      console.log(this.allAddress)
    },
    // outputAddress() {
    //   this.allAddress = this.item.data.allAddress;
    //   console.log(this.allAddress)
    // }
  },
}
</script>
