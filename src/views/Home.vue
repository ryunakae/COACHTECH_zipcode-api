<template>
  <div class="home">
    <input type="text" v-model="zipcode" maxlength="7" minlength="7" />
    <button @click="getWeatherByZip()">Zip Code</button>
    <p>Address：{{ allAddress }}</p>
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
    };
  },
  methods: {
    getWeatherByZip() {
      this.zip = this.zipcode
      // this.created()
    }
  },
async created() {
    let item = await axios.get(
      `https://apis.postcode-jp.com/api/v4/postcodes/${this.zip}?apiKey=ZCxePaJWxCZcvFWy8cuRrA01Sca4rCOZ8HsGePl`
    );
    this.allAddress = item.data.allAddress;
  }
}
</script>
