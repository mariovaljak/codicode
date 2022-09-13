<template>
  <form @submit="handleSubmit">
    <div>
      <label for="lat">lat</label>
      <input type="number" id="lat" v-model="formValues.lat" />
    </div>
    <div>
      <label for="lng">lng</label>
      <input type="number" id="lng" v-model="formValues.lng" />
    </div>
    <div>
      <label for="address">address</label>
      <input type="text" id="address" v-model="formValues.address" />
    </div>
    <div>
      <label for="house_number">house number</label>
      <input
        type="number"
        id="house_number"
        v-model="formValues.house_number"
      />
    </div>
    <div>
      <label for="post_code">post code</label>
      <input type="number" id="post_code" v-model="formValues.post_code" />
    </div>
    <div>
      <label for="city">city</label>
      <input type="text" id="city" v-model="formValues.city" />
    </div>
    <div>
      <label for="country">country</label>
      <input type="text" id="country" v-model="formValues.country" />
    </div>
    <div class="submit">
      <button class="btn2">Spremiti</button>
      <button @click="$emit('close')" class="btn3">Zatvoriti</button>
    </div>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "SubmitForm",
  data() {
    return {
      formValues: {
        lat: "",
        lng: "",
        address: "",
        house_number: "",
        post_code: "",
        city: "",
        country: "",
      },
    };
  },
  methods: {
    handleSubmit: async function (e) {
      e.preventDefault();
      try {
        const response = await axios.post(
          "http://localhost:1337/api/locations",
          { data: this.formValues }
        );
        console.log(response);
      } catch (error) {
        this.error = error;
      }
    },
  },
  emits: ["close"],
};
</script>

<style scoped>
form {
  max-width: 400px;
  margin: 15px auto;
  background: #fff;
  text-align: left;
  padding: 10px;
  border-radius: 10px;
  border: 3px solid wheat;
  box-shadow: 0 0 5px wheat;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 5px 0;
  text-transform: uppercase;
  font-size: 0.7em;
  font-weight: bold;
}

input {
  display: block;
  padding: 5px 0;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

.submit {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 0 50px;
}

.btn2 {
  background-color: #08d;
  border: 0;
  padding: 5px 15px;
  margin-top: 15px;
  color: #fff;
  border-radius: 15px;
  cursor: pointer;
}

.btn3 {
  background-color: #fa423c;
  border: 0;
  padding: 5px 15px;
  margin-top: 15px;
  color: #fff;
  border-radius: 15px;
  cursor: pointer;
}

.btn2:active {
  background-color: #06b;
}

.btn3:active {
  background-color: #ba2c0d;
}
</style>