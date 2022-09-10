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
      <label for="house_number">house_number</label>
      <input
        type="number"
        id="house_number"
        v-model="formValues.house_number"
      />
    </div>
    <div>
      <label for="post_code">post_code</label>
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
    <div>
      <button class="submit">Spremi</button>
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
  //   async mounted() {
  //     try {
  //       const response = await axios.get("http://localhost:1337/api/locations");
  //       this.formValues = response.data;
  //     } catch (error) {
  //       this.error = error;
  //     }
  //   },
  methods: {
    handleSubmit: async function (e) {
      e.preventDefault();
      try {
        const response = await axios.post(
          "http://localhost:1337/api/locations",
          this.formValues
        );
        console.log(response.data);
      } catch (error) {
        console.log(error.response);
      }
    },
  },
};
</script>

<style scoped>
form {
  max-width: 500px;
  width: 100%;
  background: #fff;
  padding: 25px 30px;
  border-radius: 5px;
}

.submit {
  background-color: #08d;
  border-radius: 12px;
  border: 0;
  box-sizing: border-box;
  color: #eee;
  cursor: pointer;
  font-size: 10px;
  height: 30px;
  margin-top: 20px;
  text-align: center;
  width: 30%;
  text-transform: uppercase;
}

.submit:active {
  background-color: #06b;
}
</style>