<template>
  <div class="heading">
    Spremljene lokacije
    <div class="table" v-for="location in locations" :key="location.id">
      {{ location.attributes.lat }}
      {{ location.attributes.lng }}
      {{ location.attributes.address }}
      {{ location.attributes.house_number }}
      {{ location.attributes.post_code }}
      {{ location.attributes.city }}
      {{ location.attributes.country }}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "History",
  data() {
    return {
      locations: [],
    };
  },
  async mounted() {
    try {
      const response = await axios.get("http://localhost:1337/api/locations");
      this.locations = response.data.data;
    } catch (error) {
      this.error = error;
    }
  },
};
</script>

<style scoped>
.heading {
  color: white;
  text-transform: uppercase;
}
.table {
  color: white;
  text-transform: lowercase;
}
</style>

